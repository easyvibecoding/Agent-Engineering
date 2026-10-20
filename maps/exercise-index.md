# 84 題索引

題目修訂：2026-10-21。14 天必做 Q01、Q03、Q05，共 42 題；7 天必做 Q01、Q05，共 28 題。每題的情境與交付已寫在題幹，先自答再看提示。

| 題號 | 類型 | 這題在問什麼 | 14 天 |
| --- | --- | --- | --- |
| [C01-Q01](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q01) | 概念重建 | 把本章四個工作分給適當角色：算 12 天、建議追問拆封、讀 T-1042、拒絕關單。模型與 harness 各做哪些？ | 必做 |
| [C01-Q02](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q02) | 方案比較 | 比較「CSV 改欄名」與 T-1042 判斷：哪一個先用固定流程，哪一個可能需要看結果再選下一步？什麼條件會讓你改選？ | 延伸 |
| [C01-Q03](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q03) | 軌跡診斷 | 另一張教學工單：模型輸出『已寄送回覆』，紀錄卻只有產生草稿，沒有寄信工具。應向客服說什麼？下一個要查什麼？ | 必做 |
| [C01-Q04](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q04) | 架構設計 | 畫一張 T-1042 的責任圖，至少包含任務、模型、工具、權限檢查與結果檢查。標出模型不能自己決定的兩件事。 | 延伸 |
| [C01-Q05](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q05) | 面試口答 | 用 T-1042 向面試官解釋：模型很強，為什麼還需要 harness？ | 必做 |
| [C01-Q06](../chapters/foundations/01-agent-and-harness/exercises/README.md#c01-q06) | 未來 Lab 規格 | 只寫未來練習規格：以 T-1042 為輸入，列出允許動作、交付內容和三個測試情境。不要建立程式。 | 延伸 |
| [C02-Q01](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q01) | 概念重建 | 用 T-1042 各舉一個 prompt、context、memory；說明保存的筆記何時才成為本輪 context。 | 必做 |
| [C02-Q02](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q02) | 方案比較 | 只能帶五段資料：任務、D07、D14 主條款、D14 未拆封條件、兩個日期、拆封狀態、30 頁紀錄。你會如何合併與挑選？ | 延伸 |
| [C02-Q03](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q03) | 軌跡診斷 | 輸出欄位都合法，但寫著『相差 12 天，依 D07 可退，且商品未拆封』。指出兩個內容問題，說明各查哪份資料。 | 必做 |
| [C02-Q04](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q04) | 架構設計 | 把長對話縮成五行交接，供另一輪處理 T-1042；列出你刻意不省略的兩項資訊。 | 延伸 |
| [C02-Q05](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q05) | 面試口答 | 向面試官說明：為什麼 context 很大，仍要挑選資料？請用 D07／D14 解釋。 | 必做 |
| [C02-Q06](../chapters/foundations/02-llm-and-context/exercises/README.md#c02-q06) | 未來 Lab 規格 | 只設計練習：比較全量、固定摘要、按需讀原文三種資料袋。寫控制變因與三種錯誤案例。 | 延伸 |
| [C03-Q01](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q01) | 概念重建 | 為 read_ticket(T-1042) 寫一份輸入與結果說明。結果需能區分『未知拆封』和『未拆封』。 | 必做 |
| [C03-Q02](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q02) | 方案比較 | 比較 execute(action) 和 read_ticket／close_ticket／refund 三個工具。哪種比較容易限制本輪只讀？拆工具的代價是什麼？ | 延伸 |
| [C03-Q03](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q03) | 軌跡診斷 | 搜尋回 10 筆，另有 has_more=true、next_cursor=page-2。模型卻說『全部只有 10 筆』。該修模型行為、介面，還是兩者？ | 必做 |
| [C03-Q04](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q04) | 架構設計 | 把缺 ticket_id、讀取無權限、讀取暫時失敗、關單回覆逾時分成四列，寫各自下一步與停止條件。 | 延伸 |
| [C03-Q05](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q05) | 面試口答 | 用讀 T-1042 的例子解釋：什麼叫對 Agent 友善的工具介面？ | 必做 |
| [C03-Q06](../chapters/agent-core/03-tool-contracts/exercises/README.md#c03-q06) | 未來 Lab 規格 | 只寫工具練習規格：合法讀取、未知欄位、無權限、分頁、暫時失敗、寫入結果未知各怎麼驗收？ | 延伸 |
| [C04-Q01](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q01) | 概念重建 | 用本章案例列出 loop 的一步一步流程，並分開寫本輪交付狀態與退貨資格狀態。 | 必做 |
| [C04-Q02](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q02) | 方案比較 | 將『辨識是否退貨問題』『依順序查資料』『補上漏掉的引用』分別對到 routing、plan-and-execute、evaluator-optimizer，說明為什麼。 | 延伸 |
| [C04-Q03](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q03) | 軌跡診斷 | 教學軌跡：連讀三次 T-1042，版本都 r3、拆封都未知；模型要求再讀十次。下一步應做什麼，如何判定停滯？ | 必做 |
| [C04-Q04](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q04) | 架構設計 | 畫出執行中、等待資料、等待核准、取消與完成的轉移；說明取消時外部操作可能怎樣。 | 延伸 |
| [C04-Q05](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q05) | 面試口答 | 用 T-1042 回答：你如何防止 Agent 無限循環？ | 必做 |
| [C04-Q06](../chapters/agent-core/04-agent-loop-and-planning/exercises/README.md#c04-q06) | 未來 Lab 規格 | 只設計五條 loop 練習：資料完整、缺資料、停滯、核准拒絕、使用者取消。每條指定停在哪個狀態。 | 延伸 |
| [C05-Q01](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q01) | 概念重建 | 用 D07／D14 分別說明檢索、重新排序與生成在做什麼；哪一步不能憑空找回缺席的 D14？ | 必做 |
| [C05-Q02](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q02) | 方案比較 | 商品碼查詢與『買了快兩週能退嗎』，你各用什麼搜尋起步？如何公平比較改善？ | 延伸 |
| [C05-Q03](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q03) | 軌跡診斷 | 變體：D14 片段 A 只有 14 天，B 才有未拆封；系統只取到 A，卻回答『12 天一定可退』。問題在哪？怎樣補證據？ | 必做 |
| [C05-Q04](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q04) | 架構設計 | 為 D14 設計片段要保留的資訊，讓客服能從答案回到原文；再寫一個測試漏例外的問題。 | 延伸 |
| [C05-Q05](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q05) | 面試口答 | 用這個客服例子回答：RAG 能幫什麼，為什麼仍可能答錯？ | 必做 |
| [C05-Q06](../chapters/knowledge/05-retrieval-and-rag/exercises/README.md#c05-q06) | 未來 Lab 規格 | 只寫本機檢索練習規格：D07、D14 與受限附件放本章，安排五個測試，無需 hosted file search。 | 延伸 |
| [C06-Q01](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q01) | 概念重建 | 把『這輪資料袋』『T-1042 待問拆封』『客服偏好短答』『D14 來源』分成 context、任務狀態與長期資訊，並說何時失效。 | 必做 |
| [C06-Q02](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q02) | 方案比較 | 何時只載入摘要，何時回看原始紀錄？請用『草稿已交但不知道有沒有寄送』作例子。 | 延伸 |
| [C06-Q03](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q03) | 軌跡診斷 | 變體：昨天 r3 摘要寫拆封未知；今天 r4 客戶回覆已拆封。助理卻沿用舊摘要說可以退。如何修正進度與答案？ | 必做 |
| [C06-Q04](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q04) | 架構設計 | 寫一份六行 T-1042 交接，讓另一輪不必重讀全部對話，仍能安全接續。 | 延伸 |
| [C06-Q05](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q05) | 面試口答 | 用工作桌、資料櫃與進度快照解釋 context、memory、checkpoint；補一句類比的限制。 | 必做 |
| [C06-Q06](../chapters/knowledge/06-memory-and-state/exercises/README.md#c06-q06) | 未來 Lab 規格 | 只設計恢復練習：在讀工單後、交草稿後、外部操作後中斷，如何判斷要重做什麼？ | 延伸 |
| [C07-Q01](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q01) | 概念重建 | 把 T-1042 的客戶端、Codex harness、模型與教學資料環境畫出來，並放入 thread、turn、item。 | 必做 |
| [C07-Q02](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q02) | 方案比較 | 一次產生草稿報告，和有核准按鈕及歷史的客服工作台，分別選哪個入口？列一項新增維護責任。 | 延伸 |
| [C07-Q03](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q03) | 軌跡診斷 | 教學事件：thread.started → turn.started → 文字片段『可以退…』→ turn/completed，status=failed。客服畫面應顯示什麼？ | 必做 |
| [C07-Q04](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q04) | 架構設計 | 設計 T-1042 唯讀任務的目錄、可讀檔案與寫入核准規則；說明為何子資料夾不能單獨保證隔離。 | 延伸 |
| [C07-Q05](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q05) | 面試口答 | 用客服工作台例子解釋 Codex SDK、app-server、Agents SDK 怎麼選。 | 必做 |
| [C07-Q06](../chapters/codex-runtime/07-codex-runtime/exercises/README.md#c07-q06) | 未來 Lab 規格 | 只設計 Codex 事件觀測練習，如何證明本輪完成、以及它沒有寄信或關單？ | 延伸 |
| [C08-Q01](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q01) | 概念重建 | 分別說出 OAuth、Responses、harness 在 T-1042 任務的工作，並說明為什麼登入成功仍不能直接推論。 | 必做 |
| [C08-Q02](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q02) | 方案比較 | 如果目標是學習每輪決策，和如果目標是快速做客服操作台，你會如何選自建 loop 或 Codex app-server？ | 延伸 |
| [C08-Q03](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q03) | 軌跡診斷 | 教學串流：HTTP 200 → 片段『可以…』→ response.failed，碼為 subscription_sharing_usage_limit_exceeded。現在可交最終答案嗎？如何保留進度？ | 必做 |
| [C08-Q04](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q04) | 架構設計 | 畫一次『模型要求讀工單』的往返，標出推論完成、工具真正執行、結果進入下一輪三個時點。 | 延伸 |
| [C08-Q05](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q05) | 面試口答 | 用白話回答：用訂閱自己做 harness，和直接用 Codex，是不是同一件事？ | 必做 |
| [C08-Q06](../chapters/codex-runtime/08-subscription-oauth-and-harness/exercises/README.md#c08-q06) | 未來 Lab 規格 | 只寫訂閱 harness 練習的驗收表，至少涵蓋拒絕同意、缺 scope、更新 token、串流斷線、工具拒絕、額度中止和正常完成。 | 延伸 |
| [C09-Q01](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q01) | 概念重建 | 以 Codex 讀 D14 為例，指出 host、client、server；再各舉一個 tool、resource、prompt 的用途。 | 必做 |
| [C09-Q02](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q02) | 方案比較 | 『本 repo 不代答』『先查日期再拆封』『讀 T-1042』各放哪裡？若只有方法但沒有工具會怎樣？ | 延伸 |
| [C09-Q03](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q03) | 軌跡診斷 | 變體：server 能列出 read_ticket，但呼叫 T-1042 回無權限；Skill 又寫『必須讀到』。你應查什麼、做什麼？ | 必做 |
| [C09-Q04](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q04) | 架構設計 | 為 300 個工具畫兩階段探索：如何縮小選單，以及執行前仍需檢查什麼？ | 延伸 |
| [C09-Q05](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q05) | 面試口答 | 用客服例子說明 MCP 和 Skill 的差別，並舉一個兩者搭配的做法。 | 必做 |
| [C09-Q06](../chapters/protocols/09-mcp-skills-and-discovery/exercises/README.md#c09-q06) | 未來 Lab 規格 | 只設計本機 MCP 練習，測列舉成功、讀取成功、無權限、版本不合、必要工具缺少及 server 不可用。 | 延伸 |
| [C10-Q01](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q01) | 概念重建 | 以查店規專家說明 agent-as-tool、handoff 和 A2A 各在解決什麼問題。 | 必做 |
| [C10-Q02](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q02) | 方案比較 | 沿用教學時間 A=25 秒、B=30 秒、整合=8 秒，算串行與理想並行時間。再列兩個可能吃掉收益的因素。 | 延伸 |
| [C10-Q03](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q03) | 軌跡診斷 | A、B 都回 completed，沒有來源；兩人又覆寫同一主稿。下一步要補什麼，怎麼避免再發生？ | 必做 |
| [C10-Q04](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q04) | 架構設計 | 寫給 B 的委派，讓它不會讀錯成 T-1043；回報至少包含五項資訊。 | 延伸 |
| [C10-Q05](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q05) | 面試口答 | 用本章案例回答：多 Agent 為什麼可能更差？ | 必做 |
| [C10-Q06](../chapters/protocols/10-multi-agent-and-a2a/exercises/README.md#c10-q06) | 未來 Lab 規格 | 只設計單／多 Agent 對照練習，固定資料、工具與總預算，列三項品質和兩項資源觀測。 | 延伸 |
| [C11-Q01](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q01) | 概念重建 | 把使用者指令、D14 條款、夾帶上傳要求分成三列：各可影響什麼，不能授予什麼？ | 必做 |
| [C11-Q02](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q02) | 方案比較 | 為只讀 T-1042 與 D14 的任務列最小檔案、網路及寫入範圍；哪種新要求需重新審查？ | 延伸 |
| [C11-Q03](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q03) | 軌跡診斷 | 延伸變體：使用者核准 close T-1042、r4，模型送出 close T-1043。能沿用核准嗎？要驗證哪三項？ | 必做 |
| [C11-Q04](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q04) | 架構設計 | 畫出夾帶上傳指令到候選工具要求的路徑，在檔案、網路與核准位置標出阻擋點。 | 延伸 |
| [C11-Q05](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q05) | 面試口答 | 用這個案例回答：Agent 安全為何需要檢查工具，而不只檢查回答？ | 必做 |
| [C11-Q06](../chapters/production/11-safety-and-trust/exercises/README.md#c11-q06) | 未來 Lab 規格 | 只設計四種攻擊練習：文件注入、惡意工具描述、記憶汙染、核准目標替換。每種寫禁止結果和觀測。 | 延伸 |
| [C12-Q01](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q01) | 概念重建 | 為什麼關單超時要標結果未知？列出兩種可能的遠端狀態。 | 必做 |
| [C12-Q02](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q02) | 方案比較 | 比較 operation_id 與 attempt_id，重送時各保留或更換哪一個？ | 延伸 |
| [C12-Q03](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q03) | 軌跡診斷 | a1 已完成關單 r5，但回覆遺失，本地檢查點仍是送出。重啟後如何處理？ | 必做 |
| [C12-Q04](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q04) | 架構設計 | 設計三列恢復表：已完成、未完成、未知；每列給判斷證據與動作。 | 延伸 |
| [C12-Q05](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q05) | 面試口答 | 面試回答：你如何避免 Agent 重複執行有副作用的工具？ | 必做 |
| [C12-Q06](../chapters/production/12-reliability-and-recovery/exercises/README.md#c12-q06) | 未來 Lab 規格 | 只設計斷線測試規格，涵蓋送出前、執行後回覆前、回覆後存檔前三個中斷點。 | 延伸 |
| [C13-Q01](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q01) | 概念重建 | 把 A–F 分成通過、失敗、中斷、未跑，算兩種通過比例。 | 必做 |
| [C13-Q02](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q02) | 方案比較 | 三次結果成功、失敗、成功，至少一次成功與全部成功各代表什麼？ | 延伸 |
| [C13-Q03](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q03) | 軌跡診斷 | 報告把 E 排除後寫整套系統成功率 75%、已全面跑通，哪裡不成立？ | 必做 |
| [C13-Q04](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q04) | 架構設計 | 為 D 過期店規設計一個品質檢查和一組事件欄位。 | 延伸 |
| [C13-Q05](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q05) | 面試口答 | 模型 5 秒、工具 1 秒、人工 12 秒，模型加速一倍會怎樣？面試如何說明？ | 必做 |
| [C13-Q06](../chapters/production/13-evals-observability-and-budgets/exercises/README.md#c13-q06) | 未來 Lab 規格 | 只寫一份模型比較規格：同樣輸入、規則、重複次數與停止條件。 | 延伸 |
| [C14-Q01](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q01) | 概念重建 | 用三句話說明本系統的使用者結果、限制及驗收。 | 必做 |
| [C14-Q02](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q02) | 方案比較 | 比較單一 Agent 與多 Agent 方案，何時值得改成後者？ | 延伸 |
| [C14-Q03](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q03) | 軌跡診斷 | 設計稿寫 r3 包裝未知但已核准退貨，並用 turn/completed 證明已退款。逐項修正。 | 必做 |
| [C14-Q04](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q04) | 架構設計 | 完成一頁架構，把每個元件對應到一個失敗與驗收。 | 延伸 |
| [C14-Q05](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q05) | 面試口答 | 用兩分鐘回答：你會如何打造可靠的客服 Agent？ | 必做 |
| [C14-Q06](../chapters/synthesis/14-system-design-and-interviews/exercises/README.md#c14-q06) | 未來 Lab 規格 | 只規劃第 15–28 天的一個最小實作，列第一條通路、失敗案例與驗收證據。 | 延伸 |
