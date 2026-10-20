# 84 題索引

題目版本：2026-10-21，已按各章深化內容同步。14 天必做 Q01／Q03／Q05，共 42 題；7 天必做 Q01／Q05，共 28 題。先自答，再按需讀提示與解答。題內子問是同一題的推導步驟，不另增題號。

| 題號 | 類型 | 題目入口 | 14 天 |
| --- | --- | --- | --- |
| [C01-Q01](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q01) | 概念重建 | 把四個工作分給適當角色：算出 12 天、建議追問拆封、實際讀 T-1042 r3、拒絕關單。再補上 runtime 與 environment 各提供什麼。 | 必做 |
| [C01-Q02](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q02) | 方案比較 | 任務 A 是把 CSV「姓名」欄改成 name；欄名衝突一律回報。任務 B 是判斷 T-1042；資料只含兩個日期與包裝欄位，缺欄位一律產生固定詢問。變體 B2 才加入不固定的附件類型與來源選擇。 | 延伸 |
| [C01-Q03](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q03) | 軌跡診斷 | 另一張同樣只准草稿的教學工單有四筆合成紀錄：e1 任務=只產生草稿；e2 工具清單只有讀取與日期計算；e3 產物=reply-draft；e4 模型最終回答=「已寄送回覆」。沒有寄送工具事件，也未查外部郵件系統。 | 必做 |
| [C01-Q04](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q04) | 架構設計 | 為 T-1042 畫責任圖，至少有任務、模型、工具、執行前授權與交付檢查。輸入可有兩種：A 已附 r3 與 D14；B 尚未提供，需先讀取。 | 延伸 |
| [C01-Q05](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q05) | 面試口答 | 用 T-1042 回答：「模型很強，為什麼還需要 harness？是不是所有工作都應該做成 Agent？」 | 必做 |
| [C01-Q06](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q06) | 未來 Lab 規格 | 只寫規格，以 T-1042 r3 和 D14 為輸入，設計責任分工與驗收；不寫程式、不裝依賴。另設完整包裝資訊與越權要求兩個變體。 | 延伸 |
| [C02-Q01](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q01) | 概念重建 | 用 T-1042 各舉一個 prompt、context、memory。假設筆記「拆封待確認」已存在磁碟，但本輪尚未讀取，說明它何時才成為本輪 context；再用一句話區分 token、context window、output budget。 | 必做 |
| [C02-Q02](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q02) | 方案比較 | 只能整理成五段資料：候選有任務、D07、D14 天數主條款、D14 未拆封條件、兩個日期、拆封狀態、30 頁紀錄。可合併相關項目，不是只能選五個欄位。請為每段寫內容、來源與用途，交代不帶全文的資料如何回查。 | 延伸 |
| [C02-Q03](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q03) | 軌跡診斷 | 輸出有 ticket_id、conclusion、draft 三個合法字串，conclusion 寫「相差 12 天，依 D07 可退，且商品未拆封」，draft 寫「您的退貨已獲核准」。請分成格式、規則版本、規則運算、事實證據、業務狀態五欄檢查，指出至少兩個內容問題並寫修正草稿。 | 必做 |
| [C02-Q04](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q04) | 架構設計 | 把包含十次重複搜尋、寒暄、T-1042 r3、兩日期、D14 完整條款、拆封 unknown、只准草稿的長對話縮成五行交接。每行標來源或用途；另列兩項可刪與兩項不能刪的內容，再設計一次壓縮後驗真。 | 延伸 |
| [C02-Q05](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q05) | 面試口答 | 用兩分鐘說明：為什麼 context 很大仍要挑選資料？先用 D07／D14 給一個失敗例，再提出比較全量與整理後資料袋的方法。最後回答「既然摘要會失真，為何還要用？」 | 必做 |
| [C02-Q06](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q06) | 未來 Lab 規格 | 只寫規格：比較全量、固定摘要、按需讀原文三種資料袋。三組可讀相同來源，固定工單、問題與模型設定；設計舊版混入、摘要漏條件、工單缺資料三案。交輸入、預期判斷、觀察欄位與不通過條件，不建立程式。 | 延伸 |
| [C03-Q01](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q01) | 概念重建 | 為 read_ticket(T-1042) 寫輸入與結果契約。已知 r3 的日期為 2026-10-08／10-20，拆封沒填，任務只讀及草稿。 | 必做 |
| [C03-Q02](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q02) | 方案比較 | 比較 execute(action) 與 read_ticket／close_ticket／refund。情境 A 只有三種操作；情境 B 把工單每一欄都拆成獨立工具，已有 80 個工具。 | 延伸 |
| [C03-Q03](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q03) | 軌跡診斷 | 搜尋第一頁回 10 個唯一項目，has_more=true、next_cursor=page-2；模型說「全部只有 10 筆」。變體 A：任務是完整統計，第二頁回 4 個不重複項目且 has_more=false。變體 B：第二頁暫時失敗。假定 A 翻頁期間資料不變。 | 必做 |
| [C03-Q04](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q04) | 架構設計 | 為缺 ticket_id、讀取無權限、讀取暫時失敗、關單回覆逾時各寫一列。最後一列是獨立變體：操作另有明確授權，但沒收到可靠結果，不適用基礎只讀案例。 | 延伸 |
| [C03-Q05](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q05) | 面試口答 | 用讀 T-1042 的例子，兩分鐘解釋什麼叫對 Agent 友善的工具介面。面試官追問：「Schema 已經合法，為什麼還要後端檢查？」 | 必做 |
| [C03-Q06](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q06) | 未來 Lab 規格 | 只寫工具練習規格，涵蓋合法讀取、未知欄位、無權限、分頁、暫時失敗、寫入結果未知六類。不得建立程式、呼叫真實工單或登入。 | 延伸 |
| [C04-Q01](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q01) | 概念重建 | 用 T-1042 r3 從接收任務到交付草稿列出 5–7 個事件。每列寫已知／未知、候選動作與選它的理由。最後分開本輪交付、業務進度與外部效果。 | 必做 |
| [C04-Q02](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q02) | 方案比較 | 把「辨識退貨問題」「依序查兩個已知來源」「看到 D07 後改找有效版」「補草稿漏掉的拆封條件」分別對到 routing、plan-and-execute、ReAct、evaluator-optimizer。另回答：若兩個固定讀取即可完成，是否仍需四種機制全部上場？ | 延伸 |
| [C04-Q03](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q03) | 軌跡診斷 | 合成軌跡：連讀三次 T-1042，都是 r3、拆封未知；沒有其他合法資料來源。模型提議再讀十次。另有草稿「12 天內，已符合退貨」。請標出兩種不同缺陷，指定下一步、停止原因，以及各自的驗收證據。 | 必做 |
| [C04-Q04](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q04) | 架構設計 | 設計執行中、等待資料、等待核准、取消、本輪完成的轉移表。基礎任務只讀及草稿；另設一個獨立變體：使用者要求具體寫入，但尚缺所需核准。給每條轉移事件與守門條件。再假設取消到達時已有工作送出，說明記錄什麼。 | 延伸 |
| [C04-Q05](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q05) | 面試口答 | 用 T-1042 在兩分鐘回答「如何防止 Agent 無限循環？」需涵蓋進展、硬上限、缺資料的合法下一步。追問：為何限制 10 輪仍不夠？若自評說需要第 11 輪呢？ | 必做 |
| [C04-Q06](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q06) | 未來 Lab 規格 | 只設計五條 loop 練習：資料完整、缺資料、停滯、核准拒絕、使用者取消。每條寫輸入變體、事件、預期狀態、停止原因與不得發生的動作。資料完整案明示改成未拆封；核准拒絕案是獨立寫入變體。 | 延伸 |
| [C05-Q01](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q01) | 概念重建 | 給定候選只有 D07 與 D14-A，D14-B 沒有進入候選；另一輪候選 A、B 都有，但輸入只放 A。分別說明檢索、重排、context 組裝與生成的責任。哪一種錯誤不能只靠重排修正？ | 必做 |
| [C05-Q02](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q02) | 方案比較 | 同一組政策有兩類查詢：①「D14 §2-B」或商品碼 SKU-1042；②「買了快兩週能退嗎」。你可以選精確／關鍵字、語意或混合檢索。請說明起步方案與換方案條件，再設計公平比較方式；題目未提供實測成績。 | 延伸 |
| [C05-Q03](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q03) | 軌跡診斷 | 合成軌跡：客服身分搜尋 → 授權候選 D07、D14-A → 選用現行 A → 模型輸入只有「相差不超過 14 天」與 T-1042 r3（12 天、拆封未知）→ 回答「12 天一定可退 [D14 §2-A]」。D14-B 同節寫「上述申請限商品未拆封」。定位至少兩層問題；再回答若輸入原本已有 B，診斷會怎樣改變。 | 必做 |
| [C05-Q04](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q04) | 架構設計 | 為 D14-A／B 設計不依賴特定向量庫的片段契約。客服要能從回答回到原文；X99 管理員附件不可進入其模型輸入。另假設日後 D14 被新政策取代，說明哪些衍生資料要更新。 | 延伸 |
| [C05-Q05](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q05) | 面試口答 | 用 T-1042 回答：「RAG 能幫什麼，為什麼仍可能答錯？」再受三個追問：D14 不在候選怎麼辦？已有 B 仍答錯怎麼辦？只有三份短政策一定要向量庫嗎？ | 必做 |
| [C05-Q06](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q06) | 未來 Lab 規格 | 只寫未來本機檢索練習規格，自帶 D07、D14-A／B、客服身分與受限 X99。安排五個測試：精確查詢、口語改述、條款漏取、權限、查無規則。先有簡單基線，不建立索引程式、依賴或環境。 | 延伸 |
| [C06-Q01](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q01) | 概念重建 | 把下列資料分成「當輪輸入」「本案狀態／checkpoint」「可跨任務資訊」：這輪載入的 D14、T-1042 待問拆封、昨天草稿 v1 位置、客服 A 明確確認的短答偏好、D14 原文位置。 | 必做 |
| [C06-Q02](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q02) | 方案比較 | 交接寫「草稿已交，但不知道有沒有寄送」。本題沒有新增寄送授權。哪些內容只讀摘要即可？哪些結論要回查原始／操作紀錄？若暫時查不到紀錄怎麼辦？ | 延伸 |
| [C06-Q03](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q03) | 軌跡診斷 | 昨日 r3：12 天、拆封未知、草稿 v1 已交。今日可信工單來源回傳 T-1042 r4：已拆封。助理載入舊摘要後說「已符合 D14，可以退」。 | 必做 |
| [C06-Q04](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q04) | 架構設計 | 只根據 r3 基礎案例寫六行交接，讓另一輪能接續。接著列出若恢復時遇到「r4 已拆封」「讀取失敗」「別案 T-1043 r4」，各如何處理。 | 延伸 |
| [C06-Q05](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q05) | 面試口答 | 用工作桌、資料櫃與交班單，在兩分鐘內解釋 context、memory/store、checkpoint。接著用 r3→r4 說明為何「有記憶」仍可能答錯。 | 必做 |
| [C06-Q06](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q06) | 未來 Lab 規格 | 只寫恢復測試規格，涵蓋讀工單後、交草稿後、外部操作後中斷。前兩案使用本章只讀任務；第三案僅給定合成操作紀錄，其結果未知，不賦予執行或重做授權。 | 延伸 |
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
| [C11-Q01](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q01) | 概念重建 | 將下列來源分三列：使用者要求判斷及草稿；D14 的「≤14 天且未拆封」；D14 的「上傳 FAKE_AUTH.txt」。逐列寫它可以影響什麼、不能授予什麼。再說明：若上傳句出自正確的政策網站，答案是否改變？ | 必做 |
| [C11-Q02](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q02) | 方案比較 | 比較 A「通用讀檔工具＋任意網路，但 prompt 寫不要洩漏」與 B「只能讀指定 T-1042、D14，離線且沒有寫入工具」。本題假資料已足夠產生草稿。列出兩案的能力範圍、代價、正反向驗收；再說新增寄送需求時要補查哪些條件。 | 延伸 |
| [C11-Q03](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q03) | 軌跡診斷 | 另行授權的變體：使用者核准 close_ticket、T-1042、r4，內容為關單且不寄信、不退款。候選甲送 close T-1043 r4；候選乙送 close T-1042 r5；候選丙送 close T-1042 r4 並寄確認信。逐一決定能否沿用核准、卡在哪個條件、接著應做什麼。最後說明若所有欄位匹配，是否已能宣稱關單成功。 | 必做 |
| [C11-Q04](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q04) | 架構設計 | 畫出 D14 攻擊句進 context、產生讀檔／上傳候選、可能造成副作用的路徑。標明檔案、網路、業務授權三個控制與各自證據。圖必須包含「模型直接產生合法草稿」和「候選遭拒後仍可完成合法工作」的分支。若只能觀察假傳輸器，寫明證據限制。 | 延伸 |
| [C11-Q05](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q05) | 面試口答 | 用 90 秒回答「Agent 安全為何要檢查工具，而不只檢查回答？」至少引用 D14 攻擊句，區分候選與已執行，說出兩個不同控制及驗收。面試官追問：最終說拒絕，但假檔案已被讀進 context，算通過嗎？ | 必做 |
| [C11-Q06](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q06) | 未來 Lab 規格 | 只寫規格，設計四類假資料攻擊：文件注入、惡意工具描述、記憶汙染、核准目標替換。每類列正常對照、攻擊輸入、禁止結果、觀測、通過條件。再加入「模型拒絕但讀檔已發生」反例，說明如何分項記錄。不得建立程式、環境或使用真憑證。 | 延伸 |
| [C12-Q01](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q01) | 概念重建 | a1 關單要求超時。本地只記到 preparing，還未查服務端。請列出至少兩種可能的遠端狀態，說明為何此時不能標記「關單失敗」。再分別寫一段給使用者的超時當下訊息、查到完成後訊息。 | 必做 |
| [C12-Q02](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q02) | 方案比較 | 請畫出 close-T1042-01 的 a1 與假設需要的 a2 欄位表，列 operation_id、attempt_id、target、expected_version、內容。說明重送時什麼不變、什麼會變。再回答：遠端去重紀錄已過期時，只保留原 ID 還夠嗎？ | 延伸 |
| [C12-Q03](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q03) | 軌跡診斷 | 合成紀錄：t1 本地保存 close-T1042-01／a1／T-1042／r4；t2 遠端已關成 r5；t3 回覆遺失並當機；t4 重啟只見 t1。錯誤提案是「改用 close-T1042-02，讀最新版本後再關」。請找出兩個問題，寫恢復順序。另變體：只讀到 closed r5，操作歷史查不到，還能宣稱原操作由你完成嗎？ | 必做 |
| [C12-Q04](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q04) | 架構設計 | 為本章關單設計恢復決策表，至少涵蓋：原操作已成功、明確拒絕且無效果、仍處理中、僅工單 closed、查詢持續失敗。原核准只綁 T-1042 r4；若尚未執行但工單被他人更新，該如何處理？ | 延伸 |
| [C12-Q05](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q05) | 面試口答 | 兩分鐘回答：「你如何避免 Agent 重複執行有副作用的工具？」先用 a1 關單成功但回覆遺失說明，再比較版本檢查、去重、取消與補償的責任。最後交代跨資料庫與寄信系統時，為什麼不能只承諾 exactly once。 | 必做 |
| [C12-Q06](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q06) | 未來 Lab 規格 | 只設計故障注入與驗收契約，不建立程式或環境。覆蓋：明確送出前、遠端執行後回覆前、回覆到達後落盤前。再加入版本衝突與查詢一直失敗兩案。所有資料是假工單。 | 延伸 |
| [C13-Q01](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q01) | 概念重建 | 根據正文六案：A/B/C 通過，D 因 D07 失敗，E 在可評答案前配額中斷，F 未啟動。每案本次只安排一次 trial。列出預定、已嘗試、已評分、通過數；計算兩種比例，並寫一句不能下的結論。 | 必做 |
| [C13-Q02](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q02) | 方案比較 | 同一題三次完成且可評分的結果為通過、失敗、通過。解釋 pass@3 與 pass^3 各問什麼；若工作是人工挑選草稿，與每次都會對外執行的自動關單，應分別看重什麼？不能假設三次能估計未來精確機率。 | 延伸 |
| [C13-Q03](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q03) | 軌跡診斷 | 某報告寫：「E 是配額問題所以刪除；A–D 三案成功，成功率 75%，已全面跑通六案。D14 已進 D 的候選，所以 D 失敗一定是檢索沒找到新版。」F 其實未跑。逐句診斷並改寫報告，給 D 的第一個調查方向。 | 必做 |
| [C13-Q04](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q04) | 架構設計 | 為 D 設計品質檢查與事件：工具回傳 D07、D14，D14 生效日 10/01；Agent 最終用 D07 拒絕 12 天的申請。請設必要 rubric、事件關聯欄位和兩種可能根因。再設一個能考倒「只看是否有引用」grader 的校準樣本。 | 延伸 |
| [C13-Q05](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q05) | 面試口答 | 合成流程嚴格依序：模型 5 秒、工具 1 秒、必要人工確認 12 秒。只把模型時間減半，其他不變。用兩分鐘說明總時間、改善幅度、下一個優化方向，以及能否推算訂閱配額或金額節省。 | 必做 |
| [C13-Q06](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q06) | 未來 Lab 規格 | 只寫模型／harness 比較規格，不建立程式。使用六案固定輸入，方案甲乙各預定每案三個 trial；可能出現配額中斷。規定公平比較、狀態分類、評分校準、預算停止、結果保存及何時擴大回歸。 | 延伸 |
| [C14-Q01](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q01) | 概念重建 | 請用三句話分別說明使用者結果、不可突破的限制、如何驗收。已知 T-1042 r3 日期差 12 天，D14 要求 ≤14 天且未拆封，包裝未知。 | 必做 |
| [C14-Q02](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q02) | 方案比較 | 方案 A：單一 Agent 明確讀取一筆工單與有效店規。方案 B：兩個 worker 分讀工單與店規，再由整合者寫草稿。現在資料很少，沒有延遲實測。請選初版方案，列兩項收益／代價；再提出一個值得換方案的需求變化及公平比較方法。 | 延伸 |
| [C14-Q03](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q03) | 軌跡診斷 | 審查以下設計稿：①查詢目標 T-1042，但來源註記 T-1043 r3；②r3 包裝未知，結論「日期 12 天，所以已核准退貨」；③工具清單僅讀取，但草稿寫「已退款」；④以 turn/completed、turn.status=completed 當退款成功證據。四行分別寫問題、缺少的證據、修正動作。 | 必做 |
| [C14-Q04](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q04) | 架構設計 | 請依正文輸入做一頁架構：需求與範圍；資料路徑；責任；狀態；至少四項風險及驗收。另處理三個分支：正確 r3 缺拆封資料、讀取暫時失敗、候選關單。每個元件寫明「若拿掉它，會出現什麼錯」。 | 延伸 |
| [C14-Q05](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q05) | 面試口答 | 請用兩分鐘回答「如何打造可靠的客服 Agent？」以 T-1042 r3 說明，不逐個列名詞。接著用十分鐘提綱列出需求追問、失敗、驗收與擴充。最後加一句誠實描述目前成果的履歷用語。 | 必做 |
| [C14-Q06](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q06) | 未來 Lab 規格 | 只規劃第 15–28 天第一條可驗收通路：假工單 r3＋D14→條件式草稿。列每日階段與退出條件，至少含缺資料、舊規則、錯 ID、越權候選、暫時讀取失敗五種驗收。說明訂閱路線如何選、事件留哪些、哪些擴充延後。 | 延伸 |
