# 08 · 訂閱 OAuth、Responses 與自建 Harness：教學與案例

## 先抓住一個問題

**我想自己決定 Agent 的每一步，能否用合格的訂閱授權取得推論，再自己接工具？**

上一章讓 Codex 管理模型與工具循環。本章把這個循環攤開，讓你看到登入、推論、工具執行、進度保存各由誰負責。學會本章的標準，是能看著事件表判斷「現在可以做什麼」，而不只是知道一個 endpoint。

**核心讀法：**讀到「最後交付與停止」並做 Q01、Q03、Q05；「恢復」「限制」可先抓決策表，第二輪再深讀。這章只做設計推演，不啟動 OAuth、模型請求或 lab。

## 把題目放到桌上

合成客服案例：T-1042 r3，2026-10-08 購買、10-20 申請，相差 12 天。D14 自 10-01 生效，取代舊 D07；條件是日期差不超過 14 天，**且未拆封**。r3 的拆封狀態未知。使用者只要判斷與草稿，沒有寄送、關單或退款授權。詳見[共同案例](../../../maps/course-story.md)。

你要做的是本機客服 app：自己決定讀哪張工單、帶哪些歷史、何時停。若 app 符合目前 preview 的適用條件，可以請使用者同意使用其 ChatGPT 方案額度。這個授權不會提供使用者的 ChatGPT 對話，也不會提供客服系統的讀取權。[官方 overview](https://developers.openai.com/siwc/token-sharing-open-source)

## 名詞先換成人話

| 名詞 | 人話 | 本例要檢查什麼 |
| --- | --- | --- |
| OAuth | 讓使用者授權某個 app 的流程 | 這個客服 app 獲准使用方案了嗎？ |
| ID token | 經驗證後用來辨認登入者的身分資料 | 回來的帳號是否就是選中的帳號？ |
| Access token | 呼叫服務時帶上的存取憑證 | 是否對應此 app 的有效授權？ |
| Granted scopes | 服務實際授予的權限集合 | 是否包含 chatgpt.tokens.use.direct？ |
| Responses | 一次模型推論的介面 | 這次輸出是文字，還是工具要求？ |
| Harness | 控制任務怎麼往下走的程式 | 要不要執行工具、再推論、暫停或交付？ |
| call_id | 某一個工具要求與其結果的配對號碼 | 工單結果是否回給讀工單那個要求？ |

## 一、先分三條路，再決定練哪一層

| 路線 | 授權與循環 | 適合的學習目標 |
| --- | --- | --- |
| 直接用原生 Codex | Codex 原生登入與既有 harness | 先學任務、工具、權限及結果驗收 |
| 自己的 app → Responses | app 取得自己的合法授權，自己管理 loop | 練事件處理、工具配對、歷史及停止 |
| 自己的 app → Codex app-server | app 管自己的 OAuth，Codex 提供既有 harness | 做客戶端、核准介面與任務整合 |

共同點是仍要驗收 T-1042 的草稿。差別是循環由誰控制。第三條路不是「沒有 harness」，而是沿用 Codex 的 harness；第二條路才是自己實作這一層。

原生 Codex 已登入，只證明其登入路線的狀態。把既有登入檔複製進自己 app，不能取代 app 的註冊、使用者同意與權限驗證。本章不讀任何真實登入檔。

## 二、自己的 app 要過哪些授權檢查

把流程想成領一張限用途的通行證。瀏覽器顯示登入成功，仍要確認回呼、身分及使用權限都屬於這次申請。下表是官方流程的概念拆解，不是要手抄一份 OAuth 實作。[Registration and sign-in](https://developers.openai.com/siwc/token-sharing-open-source/sign-in)

| 順序 | 保留或檢查什麼 | 為什麼不能省略 |
| --- | --- | --- |
| 1 · 辨認 host | 同一安裝環境保留穩定 ext_agent_host_id | 重啟不是新 host；host ID 也不是授權憑證 |
| 2 · 辨認 client | 首次用 dynamic_agent_client 入口；保存回來的 issued client_id | 入口字串不是之後交換 token 的正式 client ID |
| 3 · 起始申請 | 每次產生新的 state、nonce、PKCE verifier | 分別綁定回呼、ID token 與授權碼交換 |
| 4 · 接回呼 | 核對 state，先處理拒絕；核對註冊 client | 不能把另一個申請或帳號的結果覆蓋進來 |
| 5 · 換 token | 用 issued client_id、PKCE verifier、同一次的精確 redirect URI | 只有收到 code 不表示交換條件正確 |
| 6 · 驗身分 | 驗 ID token 簽章、issuer、audience、期限、nonce、帳號 | 能解開 JSON 不等於內容可信 |
| 7 · 驗使用權 | 讀 token response 的 granted scopes | 要求過 scope，不代表服務最後授予了它 |

state 回答「這是我剛發起的回呼嗎」；nonce 回答「這個 ID token 對應這次身分驗證嗎」；PKCE 用 verifier 證明交換授權碼的 client 持有起始申請的秘密。它們保護不同連結，不能拿同一個固定字串充當三項檢查。

首次註冊的 issued client_id 綁定使用者與當時選取的 workspace；host ID 區分執行環境。同一使用者與 workspace 的 client 可以有不同 host。換 workspace 不能只改介面標籤，必須讓註冊與身分資料保持正確對應。[官方 client／host 說明](https://developers.openai.com/siwc/token-sharing-open-source#a-client-vs-an-agent-host)

### 兩種「登入成功」要分開顯示

假設 ID token 通過檢查，但缺 chatgpt.tokens.use.direct：可以顯示「已登入，尚未啟用方案推論」，不能顯示「AI 已可用」。拒絕同意則停止該次流程，不換 code、不送推論。讓使用者之後主動重新授權，並不等於每次開 app 都強迫同意。

憑證留在 app 自己受保護的儲存位置，與教材、一般進度紀錄分開；log 只留檢查結果與必要錯誤，不留 token。原子更新憑證是指完整替換相互關聯的新值，避免一半新、一半舊；不是把 token 當教材範例提交。

## 三、完整走一次：三次推論，兩個工具結果

以下全是合成紀錄。假設 app 的授權已通過，模型亦可用。工具定義只有 read_ticket 與 read_policy；D14 要從工具讀取，不能假裝第一輪已拿到。每次 HTTP 請求都帶 store=false、stream=true 與必要 input 歷史。

### 第 0 步：先寫清任務契約

| 欄位 | 本輪值 |
| --- | --- |
| 要達成 | 依有效店規判斷條件，交詢問草稿 |
| 可用動作 | 讀 T-1042、讀適用店規、產生文字 |
| 禁止動作 | 寄送、關單、退款 |
| 交付必備 | 日期計算、兩個條件、未知、來源、未執行動作 |
| 停止條件 | 已有合格草稿；或缺授權、推論失敗、資料不足需詢問 |

這份契約由 app 檢查，不會因為模型提出 close_ticket 就自動擴權。方案推論授權與客服工具授權是兩套檢查。

### 第 1 步：模型提出讀工單要求

| 次序 | 合成事件／資料 | 此刻能下的結論 |
| --- | --- | --- |
| A1 | 發送請求 A：任務、工具定義；工單內容尚未讀取 | 開始這次推論 |
| A2 | output item 要求 read_ticket，arguments 為 T-1042，call_id=call_ticket_01 | 模型提出候選動作，尚未讀資料 |
| A3 | response.completed | A 推論成功結束；不等於客服任務完成 |
| A4 | harness 驗證工具名稱、參數、T-1042 讀取權 | 通過才可執行本機讀取 |
| A5 | 本機工具回傳 T-1042 r3、兩日期、packaging=unknown | 現在才有工單證據 |

串流中的 arguments 可能分段到達，不能看見半段 JSON 就執行。此教材採保守設計：等本次推論完成、工具要求組裝完整再執行。這是 harness 的設計選擇，不代表所有系統都必須用同樣的排程。

### 第 2 步：把要求與結果配回去，再讀店規

下一次 input 不只放一句「工單讀好了」。要帶必要任務歷史、先前模型輸出中可回放的 items，以及 call_ticket_01 的結果。模型回放需要的 reasoning items 也依模型與 SDK 文件保留；不要擅自改成自己猜的內在推理。[Function calling](https://developers.openai.com/api/docs/guides/function-calling)

以下僅展示 function call 與 output 的配對概念，**不是完整可發送請求**；實際工具封裝還要符合這條 preview 的 namespace／additional_tools 要求。

~~~text
模型要求：function_call，call_id=call_ticket_01，name=read_ticket
本機結果：function_call_output，call_id=call_ticket_01
          output={ticket_id:T-1042, revision:r3, packaging:unknown, ...}
~~~

| 次序 | 合成事件／資料 | 此刻能下的結論 |
| --- | --- | --- |
| B1 | 請求 B 帶上述配對與必要歷史 | 模型可見 r3；D14 還未讀取 |
| B2 | 模型要求 read_policy，call_id=call_policy_02 | 另一個要求，不能重用工單結果代替 |
| B3 | response.completed；本機驗權並讀店規 | B 成功；政策工具讀取另行完成 |
| B4 | 結果：D14、10-01 生效、≤14 天且未拆封；D07 已被取代 | 現在才有適用規則證據 |

call_id 要從模型要求沿用，不是從工單 ID 產生，也不是看哪份結果先回來就按順序填。若一輪有多個要求，各自配對；未識別的 call_id 要攔下查明，不能任意塞進歷史。

### 第 3 步：產生草稿，再由 harness 驗收

請求 C 帶必要歷史與 call_policy_02 結果。模型此次可以直接輸出草稿，不必為了走圖而再呼叫工具。讀到 response.completed 後，harness 檢查下面五項。

| 驗收問題 | 合格內容 |
| --- | --- |
| 日期怎麼算？ | 10/20−10/08=12 天，12≤14 |
| 是否檢查第二條件？ | r3 沒記錄拆封狀態，不能判定符合 |
| 來源對嗎？ | T-1042 r3 與 D14；不是過期 D07 |
| 有沒有越權宣稱？ | 沒有「已寄出」「已核准退款」 |
| 可以停了嗎？ | 草稿完成；業務資格仍待確認拆封狀態 |

合格交付：「依 D14，申請相隔 12 天，符合天數條件；工單尚未記載是否拆封，需先確認。草稿：『您好，請問商品是否已拆封？確認後我們才能依店規進一步判斷。』本次未寄送、關單或退款。」

**最後交付與停止：**保存三次推論狀態、兩組工具配對、來源與草稿；停止本輪。不要再查同一份 r3，期待未知會自行變成未拆封。

## 四、圖上必須容得下「沒有工具」與「失敗」

~~~mermaid
flowchart TD
    A[檢查自己的 app 授權] --> B{可使用方案推論嗎}
    B -->|否| S[保存狀態並停止]
    B -->|是| C[帶必要歷史發送推論]
    C --> D{收到哪個終止結果}
    D -->|失敗、不完整、斷線| S
    D -->|completed| E{有工具要求嗎}
    E -->|有| F{參數與本機權限通過嗎}
    F -->|是| G[執行工具並配對結果]
    F -->|否| H[記錄拒絕及原因]
    G --> I{取消、資源與進度允許繼續嗎}
    H --> I
    I -->|是| C
    I -->|否| S
    E -->|無| J{草稿符合任務契約嗎}
    J -->|是| K[交付草稿；資格仍待資料]
    J -->|否，可修正且有預算| C
    J -->|否，缺資料或無法繼續| S
~~~

工具被拒絕後，可把拒絕原因送回模型以產生替代草稿，但不必無限重試。這裡「資源允許」包含本機可管的輪數、時間與取消；不是假設 preview 接受任何通用 API 的限制參數。

## 五、反例：三個完成不能互相代替

| 錯誤做法 | 為什麼錯 | 修正後 |
| --- | --- | --- |
| HTTP 200 → 顯示「退貨核准」 | 只知道連線開始，尚未等推論終止 | 先標進行中，等終止，再驗內容 |
| response.completed → 直接交付 | 輸出可能只是 read_ticket 要求 | 先分辨工具要求與最終文字 |
| 工具成功 →「符合全部店規」 | 成功讀到 unknown，不等於未拆封 | 保留未知，產生詢問草稿 |
| 工單結果填入 call_policy_02 | 資料類型和要求對象錯配 | 用原 call_id 配對並核對工具與目標 |

初學者問：「為什麼工具明明只讀，還要驗權？」只讀仍可能讀到其他客戶的工單。先驗 T-1042 的讀取範圍，才能避免模型把猜到的 T-1043 當下一步。

另一個常見疑問：「store=false，那模型怎麼記得上一輪？」由你的 app 把必要歷史再送回。服務不保存可續接的 HTTP 對話，不代表 app 不能本機保存進度；也不代表可以把缺資料的摘要當完整工具歷史。

## 六、深挖：出錯時要恢復哪一層

不要把「重試」當作所有錯誤的答案。下表根據目前官方復原指引整理；除明確代碼外，訊息文字不宜當穩定機器碼。[Errors and recovery](https://developers.openai.com/siwc/token-sharing-open-source/errors-and-recovery)

| 情況 | 如何記錄 | 下一步與停止界線 |
| --- | --- | --- |
| 同意被拒／缺 scope | 授權流程或方案權限未啟用 | 不推論；等使用者主動選擇重新授權 |
| HTTP 200 後 response.failed | 保留實際 error.code、request ID、片段標未完成 | 不交最終答案，不執行該失敗輪的候選工具 |
| usage_limit_exceeded | 保存 subscription_sharing_usage_limit_exceeded | 暫停新請求；看官方 Usage，不猜整體額度或重設時間 |
| usage_unavailable／user_unavailable | 保存完整 subscription_sharing_… 代碼 | 保留憑證，有限次退避；耗盡次數即停 |
| unsupported_capability | 記 error.param 與請求形狀，不記 token | 修正不支援項目；不原樣重送 |
| 串流中斷，沒有終止事件 | 記未確認完成、已知資料與未執行要求 | 不視為成功；保留可恢復的任務狀態 |
| 刷新確認 invalid_grant 等終止錯誤 | 區分 refresh 與 code exchange 的階段 | 停用不可用 token，保留 issued client ID 重新授權 |
| 工具拒絕或失敗 | 推論可成功，但工具結果記拒絕／失敗 | 依原因選擇替代讀取、詢問或停止 |

usage_limit_exceeded 也可能是 app 的限制，不能據此宣稱整個訂閱用完。本教材維持訂閱優先；遇到限制先保存進度，不自動切 API key 或另一種計費。暫時網路失敗也不應刪掉可用註冊，逼使用者反覆登入。

### 更新 token 後，程序不會自動看到新環境變數

自己直接呼叫 Responses，由 app 管新請求使用更新後的憑證。若沿用官方 app-server 的 env_key 配置，app 仍負責刷新；成功更新後要重啟子程序，重新 initialize，再用保存的 thread ID 做 thread/resume。只改父程序的值，不會改掉已啟動子程序的環境。[app-server 指引](https://developers.openai.com/siwc/token-sharing-open-source/codex-app-server)

恢復的是對話，不是補發業務寫入。若某個工具在斷線前已執行，先讀其已知狀態；副作用恢復的完整設計放在第 12 章。本章基礎任務只有讀取與草稿。

## 七、深挖：preview 限制怎樣影響設計

以下是 **2026-10-21 查證**的這條 plan-usage preview，不是所有 OpenAI API 或原生 Codex 的共同限制。[Preview limitations](https://developers.openai.com/siwc/token-sharing-open-source/preview-limitations)

| 文件限制 | 對 harness 的具體影響 |
| --- | --- |
| 公開 POST https://api.openai.com/v1/responses | 不使用 ChatGPT backend-api endpoint |
| HTTP：store=false、stream=true、input 為陣列 | 自管必要歷史，完整處理終止事件 |
| HTTP 不使用 previous_response_id／conversation | 不能只存 response ID 期待下次自動接續 |
| 用 instructions 或 developer message；不接受明示 system message item | 組 context 時檢查此路線的訊息形狀 |
| Function/custom tools 用 namespaces 或 additional_tools input items | 通用 Function calling 範例不能原封不動搬入 |
| 不接受 max_tool_calls、max_output_tokens、temperature 等多個一般參數 | 自己另做可觀測的輪數／時間限制，實作前查完整表 |
| 不支援 hosted file search、image generation、Code Interpreter、native computer use、hosted MCP/connectors、Responses tool_search | 若要讀工單，設計本機受控工具；不把不支援能力寫成先決條件 |
| app-server 可經 function/custom tools 使用本機 shell、MCP、子 agent | 本機能力與 hosted Responses tools 分別驗證 |

Web search 仍受模型及帳號／workspace 政策限制，不能從「某頁列了工具」推導此帳號一定能用。本課可另用 Codex 生圖製作教材；製圖流程並不能證明這條推論路線支援 hosted image generation。

若只想學 harness，可以先用這些假事件在紙上測控制邏輯。之後真正實作，仍須驗證帳號資格、授權、所選模型與能力；模型目錄是選單資料，不是推論成功證明。

## 接著做什麼

先自答[Q01／Q03／Q05](exercises/README.md)，再用 Q04 把 call_id 連起來。能指出「誰提出要求、誰執行、誰驗收」後，下一章會把本機工具連到 MCP，並說明 Skills 為何不能替你授權。

## 來源與閱讀焦點

本章官方頁面於 **2026-10-21** 重新讀取。來源是規格／產品說明，不是本 repo 已取得 grant、已完成推論或 lab 已跑通的證據。本文的客服資料、事件 ID 與保守排程是教學設計。

- [S03 · Overview](https://developers.openai.com/siwc/token-sharing-open-source)：適用範圍、client 與 host；先讀這頁。
- [S04 · Registration and sign-in](https://developers.openai.com/siwc/token-sharing-open-source/sign-in)：回呼、state／nonce／PKCE、驗證身分與 granted scopes。
- [S05 · Models and inference](https://developers.openai.com/siwc/token-sharing-open-source/models-and-inference)：公開 endpoint、終止事件與中途配額失敗。
- [S06 · Preview limitations](https://developers.openai.com/siwc/token-sharing-open-source/preview-limitations)：參數、歷史、工具限制；實作前重查。
- [S07 · Codex app-server](https://developers.openai.com/siwc/token-sharing-open-source/codex-app-server)：RPC、token 更新、重啟與 resume。
- [S25 · Errors and recovery](https://developers.openai.com/siwc/token-sharing-open-source/errors-and-recovery)：依錯誤類型選復原，不盲目重登。
- [Function calling](https://developers.openai.com/api/docs/guides/function-calling)：call_id、工具往返與模型 output items；這是一般介面說明，能力可用性仍以上面的 preview 限制為準。

[來源版本政策](../../../references/sources.md) · [設計取捨](design-notes.md) · [回章節](README.md)
