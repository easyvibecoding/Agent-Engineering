# 來源、版本與更新政策

這份表記錄本次研究採用的第一方文件、原始論文與規格。查證基線是教材來源核對日期，不代表已替讀者帳號執行所有功能，也不是自動更新承諾。一般名詞與設計推導為原創教學整理；未重刊來源全文。

| ID | 來源 | 類型與限制 | 章 | 基線 |
| --- | --- | --- | --- | --- |
| S01 | [Agent runtimes](https://developers.openai.com/api/docs/guides/agents) | 官方產品文件；不同 runtime 的責任與資源生命週期 | 01、14 | 2026-10-19 |
| S02 | [Codex authentication](https://learn.chatgpt.com/docs/auth) | 官方產品文件；ChatGPT 訂閱與 API key 登入 | 07 | 2026-10-19 |
| S03 | [ChatGPT plan usage overview](https://developers.openai.com/siwc/token-sharing-open-source) | 官方 preview；開源／本機託管應用的訂閱授權 | 08 | 2026-10-21 |
| S04 | [Registration and sign-in](https://developers.openai.com/siwc/token-sharing-open-source/sign-in) | 官方 preview；動態 client 註冊、PKCE、授權範圍 | 08 | 2026-10-21 |
| S05 | [Models and inference](https://developers.openai.com/siwc/token-sharing-open-source/models-and-inference) | 官方 preview；公開 Responses endpoint 與完成事件 | 02、08、13 | 2026-10-21 |
| S06 | [Preview limitations](https://developers.openai.com/siwc/token-sharing-open-source/preview-limitations) | 官方 preview；參數、工具與歷史限制，實作前必重查 | 02、03、05、08、09、11 | 2026-10-21 |
| S07 | [Codex app-server with ChatGPT plan](https://developers.openai.com/siwc/token-sharing-open-source/codex-app-server) | 官方 preview；app-server、Responses provider 與 token 更新 | 07、08 | 2026-10-21 |
| S08 | [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md) | 官方產品文件；指令發現與作用範圍 | 09 | 2026-10-19 |
| S09 | [Agent Skills specification](https://agentskills.io/specification) | 公開規格；按需載入，實作支援仍須逐 runtime 查證 | 09 | 2026-10-21 |
| S10 | [MCP specification 2026-07-28](https://modelcontextprotocol.io/specification/2026-07-28) | 規範性來源；勿把規格能力當成所有 runtime 已實作 | 09、11 | 2026-10-21 |
| S11 | [A2A specification](https://a2a-protocol.org/latest/specification/) | 查證時 Latest Released Version 為 1.0.0；保留與舊版的差異 | 10 | 2026-10-21 |
| S12 | [Effective context engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | 第一方工程經驗；不是跨模型保證 | 02、05、06 | 2026-10-19 |
| S13 | [Writing effective tools](https://www.anthropic.com/engineering/writing-tools-for-agents) | 第一方工程經驗；工具設計與可評估性 | 03 | 2026-10-19 |
| S14 | [Building effective agents](https://www.anthropic.com/engineering/building-effective-agents) | 第一方架構經驗；workflow 與 Agent 模式 | 01、04、10、14 | 2026-10-19 |
| S15 | [Effective harnesses for long-running agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents) | 第一方實驗；跨 session 增量工作與交接 | 04、06、10、12 | 2026-10-19 |
| S16 | [Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) | 第一方工程經驗；task、trial、grader、outcome、trace | 01、13、14 | 2026-10-21 |
| S17 | [OWASP Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) | 社群風險框架；輔助 threat modeling，不是產品安全認證 | 03、11、14 | 2026-10-19 |
| S18 | [LangGraph persistence](https://docs.langchain.com/oss/python/langgraph/persistence) | 框架文件；checkpointer 與 store 的具體對照 | 06、12 | 2026-10-21 |
| S19 | [ReAct](https://arxiv.org/abs/2210.03629) | 原始研究；理解互動式推理與行動，不要求揭露隱藏思考鏈 | 04 | 2026-10-19 |
| S20 | [Google ADK agents](https://adk.dev/agents/) | 框架文件；Agent 類型與協作方式的跨 runtime 對照 | 10 | 2026-10-19 |
| S21 | [OpenTelemetry GenAI conventions](https://github.com/open-telemetry/semantic-conventions-genai) | 官方 GenAI 規格 repo；舊站已移轉，個別欄位穩定度依版本 | 13 | 2026-10-19 |
| S22 | [Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401) | 原始研究；RAG 基本分工，非所有檢索系統的完整規格 | 05 | 2026-10-19 |
| S23 | [Codex non-interactive mode](https://learn.chatgpt.com/docs/non-interactive-mode) | 官方產品文件；exec、JSONL、結構化輸出與原生登入 | 07 | 2026-10-21 |
| S24 | [Codex SDK](https://learn.chatgpt.com/docs/codex-sdk) | 官方產品文件；Codex SDK 與 Agents SDK 是不同介面 | 07 | 2026-10-21 |
| S25 | [Errors and recovery](https://developers.openai.com/siwc/token-sharing-open-source/errors-and-recovery) | 官方 preview；額度、資格、能力限制與 OAuth 恢復 | 08、12、13 | 2026-10-21 |
| S26 | [Codex app-server](https://learn.chatgpt.com/docs/app-server) | 官方產品文件；初始化、thread／turn／item、斜線事件與核准；與 exec JSONL 分開 | 07 | 2026-10-21 |
| S27 | [MCP 2026-07-28 architecture](https://modelcontextprotocol.io/docs/2026-07-28/learn/architecture) | 第一方架構說明；host／client／server 分工，能力宣告不等於案件授權 | 09 | 2026-10-21 |
| S28 | [Function calling](https://developers.openai.com/api/docs/guides/function-calling) | 官方通用介面文件；call_id 與工具結果關聯；不由通用工具範例推定訂閱 preview 支援 | 08 | 2026-10-21 |

## 當前實際觀察與未知

2026-10-19 本機曾讀回 codex-cli 0.160.1、Logged in using ChatGPT，以及 exec help 的 JSONL、output schema、cwd 和 resume 等入口。沒有執行模型任務，沒有為本 repo 建 OAuth app，沒有驗證 app 的帳號資格或 preview 推論。

MCP latest 查證時指向 2026-07-28；A2A 最新 released version 顯示 1.0.0。協定規格不證明特定 Codex 版本已實作全部擴充。官方目前頁面可能比本機安裝版本新。

## 更新方式

修改能力敘述前先查目前官方頁，記下版本、成熟度與變更；同步章節、題目、解答及 runtime 相容說明。API preview、OAuth、模型可用性與價格／額度在未來實作前必須重查。

研究結果需保留任務分布、基準與限制，不把單篇實驗當跨產品保證。無法確認就標為待驗證，不用歷史記憶冒充當前狀態。

本 repo 沒有排程監控或自動來源更新。

## 2026-10-21 內容修訂

全章以共同客服案例加強白話解釋、逐步判斷與銜接；S05、S06、S07、S09、S10、S11 已複核，其餘來源日期保留。案例日期、數字與工具事件是合成教學，不是訂閱路線已跑通的證據。

## 2026-10-21 逐章深化複核

第 07 章新增 S26，並複核 S23／S24，明確拆開 exec 的點號 JSONL 與 app-server 的斜線事件。SDK 依具體語言與文件判斷，不把單一套件底層概括為全部 SDK。第 06、13 章分別複核 S18、S16；新增的交接欄位、rubric 與事件表皆標為教材設計，不假稱協定要求。

第 09 章另複核 S10、S09 並補 S27，將工具探索、契約取得、本次授權及結果驗收分開。核心與選用擴充的分類不代表所選 runtime 已實作全部能力。

第 08 章複核 S03／S04／S05／S06／S07／S25，新增 S28 作工具回傳關聯的補充。授權以 token response 實際 granted scopes 為準；應用程式註冊、身分及推論 scope 各有檢查，未替讀者帳號取得資格或執行授權。
