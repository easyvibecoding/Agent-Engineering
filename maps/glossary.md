# 中英詞彙表：先知道它在做什麼

名詞是辨識問題的工具。先用第三欄的動作理解，再回正文看限制；相同名詞在不同產品的精確行為仍以官方文件為準。

| 名詞 | 白話意思 | 具體例子 | 章 |
| --- | --- | --- | --- |
| Model／模型 | 讀取這次提供的資料，產生文字或下一步建議。 | 提出「先確認是否拆封」。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Agent | 能看中間結果，再決定下一步的助理系統。 | 讀完工單後發現缺資料，改為提問。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Harness | 包住模型的執行程式，安排工具、限制與進度。 | 擋住未授權的關單要求。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Runtime／執行系統 | 讓這些機制實際運作的軟體。 | Codex 是一種可使用的執行系統。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Environment／執行環境 | 程式與資料所在的地方。 | 放教學工單的本機資料夾。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Prompt／指令 | 你要求模型做什麼。 | 判斷 T-1042，列缺漏，不准寫入。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Context／本輪上下文 | 這一次模型真正看得到的全部輸入。 | 指令、T-1042、D14 段落及工具結果。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Memory／保存的記憶 | 留在外面的資訊，需要時再讀入。 | 上次記錄的待確認拆封事項。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Compaction／歷史壓縮 | 把長對話整理成較短的交接內容。 | 保留版本與未知，不保留每次搜尋廢話。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Schema／資料形狀規則 | 檢查欄位和型別是否符合約定。 | 有 conclusion 字串，不代表結論正確。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Tool／工具 | 真正去讀檔、查資料或做操作的程式入口。 | read_ticket 讀工單。 | [03](../chapters/agent-core/03-tool-contracts/lesson.md) |
| Contract／契約 | 約好要給什麼、回什麼、失敗怎麼表示。 | ticket_id 必填，回傳同一 ID 與資料版本。 | [03](../chapters/agent-core/03-tool-contracts/lesson.md) |
| Validation／驗證 | 程式依規則檢查要求。 | ID 存在、使用者可讀，才查資料。 | [03](../chapters/agent-core/03-tool-contracts/lesson.md) |
| Side effect／副作用 | 除了回文字，外部狀態真的變了。 | 關單、寄信或退款。 | [03](../chapters/agent-core/03-tool-contracts/lesson.md) |
| Pagination／分頁 | 資料分批取回。 | 回 10 筆之外，告訴你還有下一頁。 | [03](../chapters/agent-core/03-tool-contracts/lesson.md) |
| Agent loop／工作循環 | 看資料、選動作、執行、再看結果，直到有理由停。 | 讀完發現缺拆封，改為詢問。 | [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) |
| Plan-and-execute | 先列步驟，再執行，遇新資料可改計畫。 | 先查工單，再查店規。 | [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) |
| ReAct | 讓後續動作跟著中間觀測調整的方式。 | 查不到拆封資料，就停止搜尋並提問。 | [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) |
| Routing／分流 | 按任務類型送到適當處理流程。 | 退貨問題送政策流程。 | [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) |
| Evaluator-optimizer | 依具體檢查結果修改產物。 | 引用缺 D14 段落，就補引用而非重寫一切。 | [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) |
| Retrieval／檢索 | 找可能回答問題的資料。 | 找到 D07、D14。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| RAG | 先取外部資料，再讓模型依資料回答的做法。 | 讀 D14 後解釋退貨條件。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| Chunk／片段 | 為了搜尋而切出的文件小段。 | D14 的天數段與拆封段。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| Embedding／向量表示 | 把資料變成可比較相近程度的數值表示。 | 讓『能退嗎』找到退貨政策。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| Reranking／重新排序 | 對已找出的候選再判斷相關性。 | 在候選中提高適用版的位置。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| Working context／當輪資料 | 模型眼前正在用的資訊。 | 這輪載入 T-1042 和 D14。 | [06](../chapters/knowledge/06-memory-and-state/lesson.md) |
| State／任務狀態 | 這件工作進行到哪裡、下一步缺什麼。 | 草稿已交，等待拆封回答。 | [06](../chapters/knowledge/06-memory-and-state/lesson.md) |
| Checkpoint／進度快照 | 供中斷後接續的保存記錄。 | 上次用 r3、未寄送、下一步查新回覆。 | [06](../chapters/knowledge/06-memory-and-state/lesson.md) |
| Store／長期儲存 | 跨輪或跨任務保存資訊的地方。 | 客服偏好簡短回答，與個案事實分開。 | [06](../chapters/knowledge/06-memory-and-state/lesson.md) |
| Provenance／來源 | 這項資訊從哪裡來、何時確認。 | 拆封未知來自昨天 r3，不是永久事實。 | [06](../chapters/knowledge/06-memory-and-state/lesson.md) |
| CLI／命令列介面 | 人在終端機和 Codex 互動的入口。 | 請它讀資料並解釋判斷。 | [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) |
| exec | 以一項明確任務啟動非互動工作。 | 產出一份唯讀草稿報告。 | [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) |
| SDK | 讓你的程式使用一套現成介面的套件。 | 程式啟動或接續 Codex 任務。 | [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) |
| app-server | 供自訂客戶端驅動 Codex 的通訊介面。 | 接事件、歷史和核准互動。 | [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) |
| Thread／Turn／Item | 一段互動／一次請求與工作／其中一項輸入輸出。 | 同一工單對話中，一輪查詢有多個工具和訊息 item。 | [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) |
| OAuth／授權流程 | 讓使用者明確同意 app 取得某種使用權限。 | 允許此 app 使用方案推論。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| Scope／權限範圍 | 授權結果允許做哪些事。 | chatgpt.tokens.use.direct 與登入身分不同。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| Access token／存取憑證 | 呼叫時代表已授權身分的憑證。 | 作為 Bearer 傳給支援的 endpoint。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| Responses／模型推論介面 | 送入這輪資料，取得模型文字或工具要求。 | 模型要求讀 T-1042。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| Stream／串流 | 結果以多個事件陸續到達。 | 先看到文字片段，最後才知本次推論是否成功。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| MCP | 應用與外部工具／資料溝通的協定。 | 讓不同客戶端讀同一套店規服務。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Host／使用能力的應用 | 包含模型與使用者介面的應用。 | Codex。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Client／通訊元件 | Host 裡連到某個 server 的部分。 | 把讀政策要求傳過去。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Server／提供能力的服務 | 真正暴露工具或資料的服務。 | 只提供獲准文件的店規服務。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Skill／工作方法包 | 可按需要載入的步驟與資源。 | 教助理檢查日期和拆封。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Coordinator／總負責者 | 分派工作、整合與最後檢查的人或 Agent。 | 確認兩個來源指同一張工單與版本。 | [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) |
| Worker／受派工作者 | 負責一個有邊界的子題。 | A 查店規，B 查工單。 | [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) |
| Agent-as-tool | 主 Agent 把專家當一次可呼叫能力。 | 請專家回條款後，主 Agent 繼續處理。 | [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) |
| Handoff／交接 | 將部分互動或控制移交。 | 轉由另一個助理接續對話。 | [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) |
| A2A | 不同 Agent 系統交換訊息、任務與產物的協定。 | 跨系統交接，仍需驗收結果。 | [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) |
| Prompt injection／外部指令注入 | 資料夾帶要求，誘導助理偏離原任務。 | 把政策閱讀引向上傳檔案。 | [11](../chapters/production/11-safety-and-trust/lesson.md) |
| Trust boundary／信任邊界 | 哪些來源能決定什麼的分界。 | 文件能提供條款，不能批准外傳。 | [11](../chapters/production/11-safety-and-trust/lesson.md) |
| Least privilege／最小權限 | 只給完成任務所需能力。 | 讀 T-1042，不給任意檔案或寄送。 | [11](../chapters/production/11-safety-and-trust/lesson.md) |
| Approval／操作核准 | 對具體目標與內容的同意。 | 核准關 T-1042，不代表可關 T-1043。 | [11](../chapters/production/11-safety-and-trust/lesson.md) |
| Audit／稽核記錄 | 保留能查清實際行動的資料。 | 記錄拒絕原因與工具是否執行。 | [11](../chapters/production/11-safety-and-trust/lesson.md) |
| Idempotency／冪等 | 同一個邏輯操作重送，不再造成一次新的效果 | 重送 close-T1042-01 仍是同一次關單 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Retry／重試 | 對可能恢復的失敗再試一次 | 短暫斷線後查詢原操作 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Checkpoint／檢查點 | 持久保存恢復所需的進度 | 記錄操作 ID、目標、核准與最後已知狀態 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Compensation／補償 | 以另一個操作修正已發生的效果 | 重新開單是新操作，仍需自己的授權 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Unknown outcome／結果未知 | 目前證據不足以判定成功或失敗 | 沒收到回覆，不能直接認定沒有關單 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Eval／評估 | 用事先定義的案例與標準檢查行為 | D 必須選有效 D14 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| Trial／一次試跑 | 某個案例的一次執行 | 同一案例可以重複三次 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| Grader／評分器 | 根據標準判斷結果的程序或人 | 查是否把未知說成未拆封 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| Trace／事件軌跡 | 依順序留下可觀察事件 | 讀取、候選工具、拒絕和終止原因 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| Budget／預算 | 事先限制可消耗的資源 | 時間、輪數、訂閱配額或 API 金額 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| System boundary／系統邊界 | 先講這個系統負責到哪一步 | 輸出草稿，不執行退款 | [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) |
| Invariant／不變條件 | 任何流程都不能破壞的規則 | 缺證不說已未拆封；未授權不寫入 | [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) |
| SLO／服務目標 | 想達到且可以量測的服務表現 | 提出完成時間目標，之後再測 | [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) |
| Rollout／逐步上線 | 先小範圍驗證再擴大 | 從假工單只讀試跑開始 | [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) |
| ADR／架構決策紀錄 | 保存選擇、理由與代價 | 先單一 Agent，何時才拆分工 | [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) |

## 容易混淆的補充詞

這裡只列上表之外的詞。遇到定義重疊，先指出自己在談哪一層，再用動作解釋。

| 詞 | 人話與本例 | 回讀 |
| --- | --- | --- |
| Workflow | 由程式預先決定主要路徑；日期與包裝條件固定時，普通分支也能完成，不必為缺資料就採用 Agent。 | [01](../chapters/foundations/01-agent-and-harness/lesson.md) |
| Token | 模型處理資料的單位；不是中文字數、金額或剩餘訂閱額度。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Structured output | 指定輸出形狀，方便程式讀；形狀合法，仍可能把未知誤寫為未拆封。 | [02](../chapters/foundations/02-llm-and-context/lesson.md) |
| Grounding | 每項結論能找到支持它的原文；只引到 D14 標題，還不夠支持全部退貨條件。 | [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) |
| OAuth / OIDC | 授權框架與身分驗證層；辨認出使用者，不等於自己的 app 已獲方案推論權。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| PKCE | 將授權碼交換綁到起始 client，仍需其他回呼與 token 檢查。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| SSE | 將結果拆成事件陸續送回；HTTP 成功和收到片段，還不是本次推論成功。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) |
| Capability discovery | 找出有哪些能力；列出 read_ticket，不代表本使用者可讀 T-1042。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) |
| Operation ID / Attempt ID | 前者追蹤同一件關單，後者追蹤每次傳送；伺服器仍需真正實作去重。 | [12](../chapters/production/12-reliability-and-recovery/lesson.md) |
| Outcome | 最後實際得到什麼；例如工單遠端已關閉，不能只由模型說法推定。 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |
| Task / Trial | 一個待評案例與它的一次試跑；同一案例跑三次，要保留三次結果。 | [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) |

## 完成事件先認介面

exec 的 thread.started／turn.completed 與 app-server 的 thread/started／turn/completed 是不同事件格式。app-server 還要看 turn.status；不要看到名稱有 completed 就畫成功。推論、工具、任務與業務完成的比較見[訂閱與 runtime 路線](../references/subscription-runtime.md)。
