# 中英詞彙與責任邊界

術語在不同產品可能重疊；面試先聲明定義，再用具體資料流解釋。

| 術語 | 本教材用法 | 章 |
| --- | --- | --- |
| Agent | 依觀測選擇後續行動的系統；先說明你的自主程度定義。 | [01](../chapters/foundations/01-agent-and-harness/README.md) |
| Harness | 模型外圍的控制、工具、狀態、權限與驗收機制。 | [01](../chapters/foundations/01-agent-and-harness/README.md) |
| Runtime | 讓 Agent 與 harness 機制實際運作的具體執行系統。 | [01](../chapters/foundations/01-agent-and-harness/README.md) |
| Environment | 命令、程序與檔案所在的環境；和 session 不同。 | [07](../chapters/codex-runtime/07-codex-runtime/README.md) |
| Workflow | 主要路徑由工程師安排；可內含 Agent 節點。 | [04](../chapters/agent-core/04-agent-loop-and-planning/README.md) |
| Token | 模型處理的單位，不直接等於字數、金額或訂閱額度。 | [02](../chapters/foundations/02-llm-and-context/README.md) |
| Context | 當輪可見輸入，包含指令、資料、歷史與工具。 | [02](../chapters/foundations/02-llm-and-context/README.md) |
| Compaction | 壓縮歷史以維持後續工作；需保留關鍵狀態與來源。 | [02](../chapters/foundations/02-llm-and-context/README.md) |
| Structured output | 符合指定形狀的輸出；不保證事實或業務正確。 | [02](../chapters/foundations/02-llm-and-context/README.md) |
| Tool contract | 工具的輸入、結果、前置條件、錯誤及副作用語意。 | [03](../chapters/agent-core/03-tool-contracts/README.md) |
| Grounding | 以可定位證據支撐回答；來源存在仍需支持具體結論。 | [05](../chapters/knowledge/05-retrieval-and-rag/README.md) |
| Embedding | 資料的向量表示；可用於相似搜尋，不等於理解或授權。 | [05](../chapters/knowledge/05-retrieval-and-rag/README.md) |
| Reranking | 在候選集合上重新排序，不能補回從未取到的來源。 | [05](../chapters/knowledge/05-retrieval-and-rag/README.md) |
| Memory | 可保存再取用的資訊，需要範圍、來源與失效策略。 | [06](../chapters/knowledge/06-memory-and-state/README.md) |
| Checkpoint | 恢復工作所需狀態快照，不直接證明外部操作結果。 | [06](../chapters/knowledge/06-memory-and-state/README.md) |
| Thread / turn / item | 互動容器／一次請求及工作／輸入輸出單位；精確語意依 runtime。 | [07](../chapters/codex-runtime/07-codex-runtime/README.md) |
| OAuth / OIDC | 授權框架／身分驗證層；身分有效不等於已取得推論 scope。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) |
| PKCE | 把授權碼交換綁定起始 client 的 verifier；不取代 state 與 token 驗證。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) |
| SSE | 伺服器事件串流；開始與片段不保證最後成功。 | [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) |
| MCP | 連接應用與外部工具／資料的協定，需確認版本與擴充。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/README.md) |
| Skill | 按需載入的方法、指令與資源，不自行建立工具權限。 | [09](../chapters/protocols/09-mcp-skills-and-discovery/README.md) |
| A2A | Agent 系統間互通協定；Agent Card 是宣告而非能力認證。 | [10](../chapters/protocols/10-multi-agent-and-a2a/README.md) |
| Handoff | 將部分控制或互動交給其他 Agent，需交接狀態與責任。 | [10](../chapters/protocols/10-multi-agent-and-a2a/README.md) |
| Prompt injection | 外部資料誘導系統偏離授權意圖的攻擊路徑。 | [11](../chapters/production/11-safety-and-trust/README.md) |
| Idempotency | 同一邏輯操作重複要求時不重複套用副作用，需明確契約。 | [12](../chapters/production/12-reliability-and-recovery/README.md) |
| Compensation | 對已發生操作作業務補救，不一定完整還原世界。 | [12](../chapters/production/12-reliability-and-recovery/README.md) |
| Eval / task / trial / grader | 評估／題目／一次嘗試／特定評分邏輯。 | [13](../chapters/production/13-evals-observability-and-budgets/README.md) |
| Outcome / trace | 最終實際狀態／可見執行軌跡；兩者分層驗證。 | [13](../chapters/production/13-evals-observability-and-budgets/README.md) |
| SLO | 服務目標，要有可量測範圍、分母與觀測窗口。 | [14](../chapters/synthesis/14-system-design-and-interviews/README.md) |
