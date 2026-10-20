# 08 · 訂閱 OAuth、Responses 與自建 Harness：教學與案例

你想試一次：不要讓現成助理決定所有步驟，改由自己控制「下一步」。螢幕已經顯示登入成功，你按下讀工單，卻發現還有三件事沒釐清：這個 app 獲准推論了嗎？模型真的讀了嗎？它說完成，又完成了哪一段？

接下來的合成場景會走到同一份草稿。若你把其中一個綠燈當成全部完成，介面就可能顯示「退貨核准」，但系統其實連拆封狀態都還不知道。

**先走故事：**登入那一關 → 讀工單 → 讀店規 → 驗草稿。讀完可以停；完整檢查與參數留在後面的深挖。

## 先抓住一個問題

上一章由 Codex 管理模型與工具循環。現在你要自己接手這個控制程式，也就是 harness：它決定是否執行工具、再問模型、保存進度或停止。

本章先假設自己的 app 已完成合法授權，模型可用，讓你看清循環。這是設計推演；不會啟動 OAuth 或推論，也不把假事件當執行證據。

## 把題目放到桌上

客服要你讀 T-1042，依店規判斷，再寫回覆草稿。授權只有讀取與草稿，沒有寄送、關單或退款。

[共同案例](../../../maps/course-story.md)中，工單是 r3：2026-10-08 購買、10-20 申請，相差 12 天。D14 自 10-01 取代 D07，規定 ≤14 天且未拆封；r3 拆封未知。這是讀者核對用的背景；故事裡的模型仍必須從工具取得工單與店規，不能假裝已讀。

<a id="三完整走一次三次推論兩個工具結果"></a>

## 跟著三次推論走到草稿

### 第 0 步：先寫清任務契約

在開始前，你先處理螢幕上的「登入成功」。登入能辨認使用者，但自己的 app 還要獲准使用方案推論。這種請使用者授權的流程叫 OAuth。

你要看的是服務**實際授予**的權限，也就是 granted scopes。若缺 chatgpt.tokens.use.direct，應顯示「已登入，方案推論未啟用」，先停在這裡。原生 Codex 已登入，不能代替這個 app 的註冊與同意。

下面繼續時，假設這一關已通過。你再把任務寫成一句可檢查的限制：「只讀 T-1042 與有效店規，交草稿；不寄送、不關單、不退款。」方案使用權不會順便給你客服工具的權限。

符合目前 preview 適用條件的 app，可依合法流程申請使用 ChatGPT 方案額度；這不會取得使用者的 ChatGPT 對話。[官方適用範圍](https://developers.openai.com/siwc/token-sharing-open-source)與完整 OAuth 檢查放在深挖，現在不用先背。

### 第 1 步：模型提出讀工單要求

你把任務和可用工具送入 Responses。它是這次模型推論的介面：輸出可能是回答，也可能是要求你去做一件事。

第一個畫面出現：「請呼叫 read_ticket，讀 T-1042。」接著收到 response.completed。

**停 15 秒：**此刻工單內容已讀進來了嗎？先選「已有證據」或「只有要求」，再繼續。

現在只有要求。completed 表示產生這個要求的推論結束；真正讀工單的是你的本機工具。你的 harness 先檢查名稱、參數與目標讀取權，通過後才執行。

工具回來了：T-1042 r3，兩個日期，拆封欄位是 unknown。現在才有工單證據。只讀也要驗權，因為模型可能寫錯編號，讀到另一個客戶的資料。

串流會逐段到達。半段工具參數不能拿去執行；本課選擇等 response.completed 且要求完整，再驗權與執行。這是保守的排程設計，不是假定所有系統只能這樣做。

### 第 2 步：把要求與結果配回去，再讀店規

第二次問模型前，你不能只送一句「讀好了」。模型需要知道讀到什麼，以及這份結果回答哪個要求。

第一次的工具要求帶了一個配對號碼：call_id=call_ticket_01。你回填工單結果時沿用它。call_id 連的是「這次要求與這次結果」，不是工單本身的編號。

~~~text
要求：call_ticket_01 → read_ticket(T-1042)
結果：call_ticket_01 → T-1042 r3，拆封 unknown
~~~

你帶著必要歷史再送一次推論。這次模型要求讀適用店規，號碼是 call_policy_02。等推論完成，通過工具驗權，讀回 D14：≤14 天，**且未拆封**；D07 已被取代。

**再停 15 秒：**換個返回順序的變體：假設同一輪提出兩個獨立讀取要求，政策結果先回來。你會放進第一格空位，還是放回 call_policy_02？

必須按配對號碼放回去。結果先到，不代表它回答第一個要求。把工單結果接成政策，下一輪即使語句流暢，也已經用錯證據。無法識別的 call_id 要攔下，不猜配。

這時你手上有兩份結果：r3 的未知，以及 D14 的兩個條件。還差把它們組成能交付的草稿。

### 第 3 步：產生草稿，再由 harness 驗收

第三次推論帶上必要歷史和政策結果。模型這次可直接寫草稿，不用為了流程看起來完整而再叫一個工具。

等 response.completed 後，你還要讀內容。12 天符合天數條件；但商品是否未拆封，r3 沒有答案。所以「符合全部退貨規則」仍然不成立。

合格草稿可以寫：「您好，您的申請距購買日 12 天，符合 D14 的天數條件。請問商品是否已拆封？確認後我們才能依店規進一步判斷。」

交付時附上 T-1042 r3 與 D14 的來源，說明本次未寄送、關單或退款。這一輪草稿可以完成，退貨資格仍等待資料。

**最後交付與停止：**保存三次推論狀態、兩組工具配對、來源與草稿，停在「待確認拆封」。再讀同一份 r3，不會讓 unknown 自動變成未拆封。

<a id="五反例三個完成不能互相代替"></a>

## 回頭看：三個完成不能互相代替

最短的錯路是：「登入成功 → HTTP 200 → 退貨核准。」每一個箭頭都跳過檢查。200 只表示串流開始；completed 也可能只交出一個工具要求；讀工具成功則只表示取得資料，資料可能仍是 unknown。

修正時，讓介面分別記錄授權、這次推論、工具結果與草稿交付。有人問「完成了嗎」，你就能回答「草稿已完成，資格仍待拆封資料」，而不是只回一個綠燈。

至於中途只有文字片段、最後 failed 或沒有終止事件：先標未完成，保存已知進度，別替模型補完結論。具體錯誤分類放在深挖；Q03 留給你自己推一次。

## 先在這裡停，或繼續深挖

到這裡已走完核心。可以先做 [Q01／Q03／Q05](exercises/README.md)，再回來找需要的細節。以下不是新任務，而是剛才故事裡刻意沒展開的檢查。

<a id="四圖上必須容得下沒有工具與失敗"></a>

## 深挖：圖上容得下沒有工具與失敗

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

<details>
<summary>深挖：三次推論的完整事件與回放資料</summary>

每次 HTTP 請求都帶 store=false、stream=true 和必要 input。服務不保存可續接的 HTTP 對話，由 app 保存並送回必要歷史；不能只存 response ID。也不能只用「工單已讀，可退貨」取代缺條件的資料。

| 推論 | 模型已看見什麼 | output 與本機接續 |
| --- | --- | --- |
| A | 任務、工具定義，尚無工單內容 | call_ticket_01 要求讀工單；completed 後驗權並讀 r3 |
| B | 任務、必要歷史、第一次要求及其結果 | call_policy_02 要求讀政策；completed 後驗權並讀 D14 |
| C | 必要歷史與兩次工具配對 | 可直接產生草稿；completed 後驗內容 |

正式回填用 function_call_output 搭配原 call_id。下列只展示配對概念，不是完整可發送請求；工具封裝仍依 preview 的 namespace／additional_tools 要求。

~~~text
模型要求：function_call，call_id=call_ticket_01，name=read_ticket
本機結果：function_call_output，call_id=call_ticket_01
          output={ticket_id:T-1042, revision:r3, packaging:unknown, ...}
~~~

下一次 input 要有可回放的模型 output items、工具結果與必要任務歷史。模型需要的 reasoning items 也依模型與 SDK 文件保留；不要自行編寫內在推理來代替。[Function calling](https://developers.openai.com/api/docs/guides/function-calling)

草稿驗收逐項看：日期差 12≤14；未拆封未知；來源是 r3／D14；沒有越權宣稱；交付停止但資格待資料。這五件事在模型語氣很肯定時仍然要查。

</details>

<a id="一先分三條路再決定練哪一層"></a>

## 深挖：先分三條路，再決定練哪一層

| 路線 | 授權與循環 | 適合的學習目標 |
| --- | --- | --- |
| 直接用原生 Codex | Codex 原生登入與既有 harness | 先學任務、工具、權限及結果驗收 |
| 自己的 app → Responses | app 取得自己的合法授權，自己管理 loop | 練事件處理、工具配對、歷史及停止 |
| 自己的 app → Codex app-server | app 管自己的 OAuth，Codex 提供既有 harness | 做客戶端、核准介面與任務整合 |

共同點是仍要驗收 T-1042 的草稿。差別是循環由誰控制。第三條路不是「沒有 harness」，而是沿用 Codex 的 harness；第二條路才是自己實作這一層。

原生 Codex 已登入，只證明其登入路線的狀態。把既有登入檔複製進自己 app，不能取代 app 的註冊、使用者同意與權限驗證。本章不讀任何真實登入檔。

<details>
<summary>深挖：自己的 app 從登入到獲准推論</summary>

<a id="二自己的-app-要過哪些授權檢查"></a>

## 深挖：自己的 app 要過哪些授權檢查

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

</details>

<a id="六深挖出錯時要恢復哪一層"></a>

## 深挖：出錯時要恢復哪一層

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

<details>
<summary>深挖：這條 preview 的參數與 hosted tools 限制</summary>

<a id="七深挖preview-限制怎樣影響設計"></a>

## 深挖：preview 限制怎樣影響設計

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

</details>

<details>
<summary>查詞：故事裡用過的名稱</summary>

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

</details>

## 接著做什麼

先自答 Q01、Q03、Q05；若工具結果還接不清，做 [Q04](exercises/README.md#c08-q04)。下一章把本機工具接到 MCP，繼續分清「方法寫在哪裡」與「誰真的允許它執行」。

**下次從這裡接：**

- 我目前的判斷：___ 層已完成，___ 仍未知。
- 我還不確定：___。
- 下次讀：___ 段，或先做 C08-Q___。

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
