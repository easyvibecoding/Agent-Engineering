# 84 題索引

題目版本：2026-10-21，已按各章深化內容同步。14 天必做 Q01／Q03／Q05，共 42 題；7 天必做 Q01／Q05，共 28 題。先自答，再按需讀提示與解答。題內子問是同一題的推導步驟，不另增題號。

| 題號 | 類型 | 題目入口 | 14 天 |
| --- | --- | --- | --- |
| [C01-Q01](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q01) | 概念重建 | 你準備接手這套助理。桌上有四張工作卡：算出 12 天、建議追問拆封、真的讀 T-1042 r3、拒絕關單。 | 必做 |
| [C01-Q02](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q02) | 方案比較 | 你要接三項工作：A 把 CSV「姓名」欄改成 name，衝突回報；B 判斷固定日期及包裝欄位，缺欄位一律產生固定詢問；B2 才加入不固定的附件類型及來源選擇。 | 延伸 |
| [C01-Q03](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q03) | 軌跡診斷 | 另一張同樣只准草稿的工單留下四筆合成紀錄：e1 任務=只產生草稿；e2 工具只有讀取與日期計算；e3 產物=reply-draft；e4 模型說「已寄送回覆」。沒有寄送工具事件，也還沒查外部郵件系統。 | 必做 |
| [C01-Q04](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q04) | 架構設計 | 你要畫 T-1042 的責任圖。輸入 A 已附 r3 與 D14；輸入 B 尚未提供，需要讀取。 | 延伸 |
| [C01-Q05](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q05) | 面試口答 | 面試官問：「模型很強，為什麼還需要 harness？是不是所有工作都應該做成 Agent？」 | 必做 |
| [C01-Q06](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q06) | 未來 Lab 規格 | 你收到下一階段規格任務：以 T-1042 r3、D14 寫出可驗收設計。現在不寫程式，也不裝依賴。 | 延伸 |
| [C02-Q01](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q01) | 概念重建 | **核心：**筆記「拆封待確認」存在磁碟，但這輪還沒讀。它現在是本輪 context 嗎？ | 必做 |
| [C02-Q02](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q02) | 方案比較 | **核心：**請把任務、工單與政策整理成五段輸入，可合併相關欄位。 | 延伸 |
| [C02-Q03](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q03) | 軌跡診斷 | **核心：**三個合法字串欄位裡，結論是「相差 12 天，依 D07 可退，且商品未拆封」，草稿是「您的退貨已獲核准」。先挑兩個內容問題，指出要查哪份資料。 | 必做 |
| [C02-Q04](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q04) | 架構設計 | **核心：**把本章工單、政策與任務限制整理成五行交接，讓下一輪知道目前做到哪裡。 | 延伸 |
| [C02-Q05](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q05) | 面試口答 | **核心：**用兩分鐘回答：context 很大，為什麼仍要挑選資料？用 D07／D14 舉一個錯例。 | 必做 |
| [C02-Q06](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q06) | 未來 Lab 規格 | **核心：**只寫規格：比較全量、固定摘要、按需讀原文三種資料袋。先寫三組各從哪裡開始、可以讀什麼。 | 延伸 |
| [C03-Q01](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q01) | 概念重建 | 為 read_ticket(T-1042) 寫輸入與結果契約。已知 r3 的日期為 2026-10-08／10-20，拆封沒填，任務只讀及草稿。 | 必做 |
| [C03-Q02](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q02) | 方案比較 | 比較 execute(action) 與 read_ticket／close_ticket／refund。情境 A 只有三種操作；情境 B 把工單每一欄都拆成獨立工具，已有 80 個工具。 | 延伸 |
| [C03-Q03](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q03) | 軌跡診斷 | 搜尋第一頁回 10 個唯一項目，has_more=true、next_cursor=page-2；模型說「全部只有 10 筆」。變體 A：任務是完整統計，第二頁回 4 個彼此不同、且與第一頁不重複的項目，has_more=false。變體 B：第二頁暫時失敗。假定 A 翻頁期間資料不變。 | 必做 |
| [C03-Q04](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q04) | 架構設計 | 為缺 ticket_id、讀取無權限、讀取暫時失敗、關單回覆逾時各寫一列。最後一列是獨立變體：操作另有明確授權，但沒收到可靠結果，不適用基礎只讀案例。 | 延伸 |
| [C03-Q05](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q05) | 面試口答 | 用讀 T-1042 的例子，兩分鐘解釋什麼叫對 Agent 友善的工具介面。面試官追問：「Schema 已經合法，為什麼還要後端檢查？」 | 必做 |
| [C03-Q06](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q06) | 未來 Lab 規格 | 只寫工具練習規格，涵蓋合法讀取、未知欄位、無權限、分頁、暫時失敗、寫入結果未知六類。不得建立程式、呼叫真實工單或登入。 | 延伸 |
| [C04-Q01](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q01) | 概念重建 | 先替 T-1042 r3 寫 5–7 列事件：從接任務，到草稿交付。每列只寫「看到什麼 → 下一步」。 | 必做 |
| [C04-Q02](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q02) | 方案比較 | 先替四個動作各配一種模式：辨識退貨問題；依序讀兩個已知來源；看到 D07 後改找有效版；補草稿漏掉的拆封條件。 | 延伸 |
| [C04-Q03](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q03) | 軌跡診斷 | 先看這段合成軌跡：同查詢連讀三次，都回 T-1042 r3、拆封未知，沒有其他合法來源。模型提議再讀十次。你會派下一次嗎？寫一句證據。 | 必做 |
| [C04-Q04](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q04) | 架構設計 | 先畫基礎任務：執行中、等待資料、本輪完成；箭頭上寫事件與條件。 | 延伸 |
| [C04-Q05](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q05) | 面試口答 | 先用兩分鐘回答：「用 T-1042 說明如何防止 Agent 無限循環？」 | 必做 |
| [C04-Q06](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q06) | 未來 Lab 規格 | 先列五案名稱：資料完整、缺資料、停滯、核准拒絕、使用者取消。只替第一案寫輸入與預期停止。 | 延伸 |
| [C05-Q01](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q01) | 概念重建 | 候選只有 D07、D14-A，B 沒進候選。另一輪 A、B 都找到，模型輸入卻只有 A。 | 必做 |
| [C05-Q02](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q02) | 方案比較 | 同一組政策收到兩種查詢：「D14 §2-B／SKU-1042」與「買了快兩週能退嗎」。題目沒有實測成績。 | 延伸 |
| [C05-Q03](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q03) | 軌跡診斷 | 客服搜尋得到授權候選 D07、D14-A，採用現行 A。模型輸入只有天數段與 T-1042 r3（12 天、包裝未知），回答「12 天一定可退 [D14 §2-A]」。同節 B 寫「上述申請限商品未拆封」。 | 必做 |
| [C05-Q04](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q04) | 架構設計 | 你要讓客服從 D14-A／B 的引用回到原文；X99 管理員附件不能進客服模型輸入。不指定向量庫。 | 延伸 |
| [C05-Q05](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q05) | 面試口答 | 面試官問：「RAG 能幫什麼，為什麼仍可能答錯？」請用 T-1042 回答。 | 必做 |
| [C05-Q06](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q06) | 未來 Lab 規格 | 只寫未來本機檢索規格，自帶 D07、D14-A／B、客服身分與受限 X99。先有簡單基線，不建程式、索引或環境。 | 延伸 |
| [C06-Q01](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q01) | 概念重建 | 桌上有這輪載入的 D14，櫃子裡有昨天交接。你要分清保存了什麼，以及模型眼前看見什麼。 | 必做 |
| [C06-Q02](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q02) | 方案比較 | 交接寫：「草稿已交，但不知道有沒有寄送。」本題沒有新增寄送授權。 | 延伸 |
| [C06-Q03](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q03) | 軌跡診斷 | 昨日 r3：12 天、拆封未知、草稿 v1 已交。今日可信工單來源回傳 T-1042 r4：已拆封。助理讀舊摘要後說：「已符合 D14，可以退。」 | 必做 |
| [C06-Q04](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q04) | 架構設計 | 另一輪要接手 T-1042 r3；它不會先讀完整對話。 | 延伸 |
| [C06-Q05](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q05) | 面試口答 | 有人問你：「既然有 memory，為什麼重啟還會答錯？」 | 必做 |
| [C06-Q06](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q06) | 未來 Lab 規格 | 只設計恢復測試，不寫程式。你可以先完成第一個中斷點，再加其他案例。 | 延伸 |
| [C07-Q01](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q01) | 概念重建 | 把 T-1042 的客戶端、Codex harness、模型與資料環境畫成責任圖。設定 thread=th-demo-7、turn=tr-draft-1；本輪有讀 r3、讀 D14、草稿訊息三個 item。 | 必做 |
| [C07-Q02](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q02) | 方案比較 | 情境 A：客服本機手動交一份草稿給既有腳本保存，無自訂 UI。情境 B：自訂客服工作台要顯示歷史、串流與核准要求。分別選 CLI／exec／SDK／app-server 中的起步入口。 | 延伸 |
| [C07-Q03](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q03) | 軌跡診斷 | 以下是 app-server 的合成序列：thread/started → turn/started → 讀 r3 的 item/completed → item/agentMessage/delta「可以退…」→ error → turn/completed，turn.status=failed。沒有草稿 item 的完成紀錄，也沒有寄送或關單工具事件。 | 必做 |
| [C07-Q04](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q04) | 架構設計 | 設計只讀 T-1042 任務。假定教學目錄有 inputs/ticket-r3.md、inputs/policy-d14.md，草稿先回傳畫面；另有 unrelated/ 不屬於任務。現有工具可能連到客服寫入服務。 | 延伸 |
| [C07-Q05](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q05) | 面試口答 | 用客服工作台例子解釋 Codex SDK、app-server、Agents SDK 怎麼選。面試官問：「用了 SDK，是不是 harness 和客服正確性都不用管？」 | 必做 |
| [C07-Q06](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q06) | 未來 Lab 規格 | 只設計 Codex 事件觀測練習，如何證明本輪完成，以及沒有寄信或關單？可以用完整成功、讀取後失敗、連線斷開三組合成 trace 作規格；尚不建立程式。 | 延伸 |
| [C08-Q01](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q01) | 概念重建 | 某 app 已取得通過驗證的 ID token，但 token response 的 scopes 只有 openid、profile、email。使用者的原生 Codex 另外已登入。app 想讀 T-1042 並寫草稿。 | 必做 |
| [C08-Q02](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q02) | 方案比較 | 團隊有兩個目標：A 要看懂每一輪資料如何進出；B 要盡快設計客服操作台、顯示事件並接核准。兩者都使用同一 T-1042 假資料，尚未實作。 | 延伸 |
| [C08-Q03](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q03) | 軌跡診斷 | 合成請求 R3 的事件是：HTTP 200 → response.output_text.delta「可以…」→ response.failed，error.code=subscription_sharing_usage_limit_exceeded。先前已完成的讀工單工具記錄為 T-1042 r3、packaging=unknown，沒有寫入動作。服務未提供重設時間。 | 必做 |
| [C08-Q04](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q04) | 架構設計 | 請求 A 已 completed，輸出兩個完整工具要求：read_ticket(T-1042)，call_id=call_ticket_01；read_policy(D14)，call_id=call_policy_02。工具結果可能以相反順序回來。兩工具皆只讀；app 只有本題目標的讀取權。 | 延伸 |
| [C08-Q05](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q05) | 面試口答 | 面試官問：「用訂閱自己做 harness，和直接用 Codex，是不是同一件事？既然拿到 response.completed，為什麼還沒完成任務？」 | 必做 |
| [C08-Q06](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q06) | 未來 Lab 規格 | 不執行 OAuth 或請求，只寫未來驗收矩陣。至少七類：拒絕同意、缺 scope、token 更新、串流斷線、工具拒絕、額度中止、正常完成。 | 延伸 |
| [C09-Q01](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q01) | 概念重建 | 以 Codex 讀 D14 為例，畫出 host、client、server。假服務另提供 read_policy、D14 文件、退貨判斷模板，將三者對應 tool、resource、prompt。 | 必做 |
| [C09-Q02](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q02) | 方案比較 | 三個需求是「本 repo 先讓學習者自答」「先查有效版本再算日期與拆封」「讀 T-1042」。團隊想把三者全寫進 Skill，並以 allowed-tools 宣稱可讀任何工單。 | 延伸 |
| [C09-Q03](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q03) | 軌跡診斷 | 合成事件：①工具列舉有 read_ticket；②以呼叫者客服 A 讀 T-1042，回 permission_denied；③Skill 寫「必須讀到」；④助理改查其他工單，輸出「T-1042 未拆封」。 | 必做 |
| [C09-Q04](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q04) | 架構設計 | 300 個工具分工單、店規、帳務、行銷。初次探索 8 個候選，再選 2 個詳細契約；另有同名 read_policy 指向測試店，目錄可能缺漏。 | 延伸 |
| [C09-Q05](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q05) | 面試口答 | 用兩分鐘向會寫普通函式但沒用過 MCP 的工程師，說明 MCP、Skill、AGENTS.md 的差別，並用 T-1042 示範搭配。 | 必做 |
| [C09-Q06](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q06) | 未來 Lab 規格 | 只設計獨立本機 MCP 練習，包含列舉成功、讀取成功、無權限、版本不合、必要工具缺少及 server 不可用六情況。 | 延伸 |
| [C10-Q01](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q01) | 概念重建 | 以查 D14 的專家為例，比較 agent-as-tool、handoff、A2A。主助理只需要一份政策筆記；另一個變體中，專家需要接續向使用者詢問三輪。 | 必做 |
| [C10-Q02](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q02) | 方案比較 | 合成時間 A=25 秒、B=30 秒、整合=8 秒，A/B 可獨立開始。計算串行及理想並行。另一算例：單 Agent 輸入 6,000 tokens；A/B 各 4,000、總負責者 2,000。 | 延伸 |
| [C10-Q03](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q03) | 軌跡診斷 | 合成事件：A、B 都說 completed 且未交來源。A 先寫主稿「依 7 天規則已拒絕」，B 後寫「T-1043 可退貨」，覆蓋了 A。原任務仍是 T-1042 r3、D14、只讀及草稿。 | 必做 |
| [C10-Q04](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q04) | 架構設計 | 寫給 B 的委派：只讀 T-1042 r3，取得日期及包裝資料，禁止改主草稿或工單。變體一：回報 T-1043；變體二：實際已是 r4。 | 延伸 |
| [C10-Q05](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q05) | 面試口答 | 用本章案例回答：多 Agent 為什麼可能更差？你只有兩分鐘，請選一條具體失敗因果鏈，並提出公平驗證方式。 | 必做 |
| [C10-Q06](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q06) | 未來 Lab 規格 | 只設計單／多 Agent 對照，不建立程式。兩組均用相同 T-1042 r3、D14、D07 假資料與只讀工具；加入錯 ID、漏條款、worker 失敗和主稿衝突。 | 延伸 |
| [C11-Q01](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q01) | 概念重建 | **核心：**用三列寫下「使用者的草稿要求」「D14 的退貨條件」「D14 的上傳要求」。每列只補一句：它能決定什麼，不能批准什麼？ | 必做 |
| [C11-Q02](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q02) | 方案比較 | 本題有兩案：A 可通用讀檔與任意上網，只在 prompt 寫不要洩漏；B 只讀 T-1042、D14，離線且沒有寫入工具。假資料已足夠產生草稿。 | 延伸 |
| [C11-Q03](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q03) | 軌跡診斷 | 這題才新增授權：使用者核准 close_ticket、T-1042、r4，只關單，不寄信、不退款。 | 必做 |
| [C11-Q04](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q04) | 架構設計 | **核心：**先畫三個節點：D14 進 context、工具候選、實際效果。再把檔案、網路與業務授權檢查放到應在的位置，每個控制寫一種證據。 | 延伸 |
| [C11-Q05](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q05) | 面試口答 | **核心：**用 90 秒回答「為何要檢查工具，而不只檢查回答？」先沿 D14 上傳句說明候選與實際效果，再選兩個控制說怎樣驗收。 | 必做 |
| [C11-Q06](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q06) | 未來 Lab 規格 | **核心：**只寫規格，先完成「文件注入」一列：正常對照、攻擊輸入、禁止結果、觀測、通過條件。用假資料，不建立程式或環境。 | 延伸 |
| [C12-Q01](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q01) | 概念重建 | a1 關單要求超時，本地只記到 preparing，還未查服務端。 | 必做 |
| [C12-Q02](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q02) | 方案比較 | 1. **先做：**畫 a1 與假設需要的 a2 兩列，說明 close-T1042-01 與傳送編號哪些變、哪些不變。 | 延伸 |
| [C12-Q03](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q03) | 軌跡診斷 | 合成紀錄：t1 保存 close-T1042-01／a1／T-1042／r4；t2 遠端關成 r5；t3 回覆遺失並當機；t4 重啟只見 t1。 | 必做 |
| [C12-Q04](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q04) | 架構設計 | 1. **先做：**替「成功」「明確無效果」「未知」各寫證據與下一步。 | 延伸 |
| [C12-Q05](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q05) | 面試口答 | 先用兩分鐘回答：「你如何避免 Agent 重複執行有副作用的工具？」用 a1 已完成但回覆遺失帶入，說明機制前提和一個驗收方法。 | 必做 |
| [C12-Q06](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q06) | 未來 Lab 規格 | 只寫規格，不建程式或環境；所有資料是假工單。 | 延伸 |
| [C13-Q01](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q01) | 概念重建 | 根據合成六案：A/B/C 通過，D 因 D07 失敗，E 在可評答案前配額中斷，F 未啟動。每案只安排一次。 | 必做 |
| [C13-Q02](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q02) | 方案比較 | 同一題三次完成且可評分，結果為通過、失敗、通過。 | 延伸 |
| [C13-Q03](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q03) | 軌跡診斷 | 你看到這份合成報告： | 必做 |
| [C13-Q04](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q04) | 架構設計 | 固定事實：工具已回傳 D07、D14，D14 自 10/01 生效；Agent 最終用 D07 拒絕 12 天申請。基礎 r3 拆封仍未知，授權只讀與草稿。 | 延伸 |
| [C13-Q05](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q05) | 面試口答 | 合成流程嚴格依序：模型 5 秒、工具 1 秒、必要人工確認 12 秒。只把模型時間減半，其他不變。 | 必做 |
| [C13-Q06](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q06) | 未來 Lab 規格 | 只寫比較規格，不建立程式。方案甲乙都使用六案固定輸入，各預定每案三個 trial；途中可能配額中斷。 | 延伸 |
| [C14-Q01](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q01) | 概念重建 | 先寫第一句：使用者最後拿到什麼？再各補一句限制與驗收。已知 T-1042 r3 日期差 12 天，D14 要求 ≤14 天且未拆封，包裝未知。 | 必做 |
| [C14-Q02](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q02) | 方案比較 | 方案 A：單一 Agent 明確讀取一筆工單與有效店規。方案 B：兩個 worker 分讀工單與店規，再由整合者寫草稿。現在資料很少，沒有延遲實測。 | 延伸 |
| [C14-Q03](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q03) | 軌跡診斷 | 審查以下設計稿，每次只處理一行： | 必做 |
| [C14-Q04](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q04) | 架構設計 | **先做：**沿正文寫一頁草稿：需求→資料→判斷→交付，旁邊標出誰負責。 | 延伸 |
| [C14-Q05](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q05) | 面試口答 | 請用兩分鐘回答「如何打造可靠的客服 Agent？」以 T-1042 r3 說明，不逐個列名詞。 | 必做 |
| [C14-Q06](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q06) | 未來 Lab 規格 | 只規劃第 15–28 天第一條可驗收通路：假工單 r3＋D14→條件式草稿。 | 延伸 |
