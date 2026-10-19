# 可追蹤知識地圖

知識完整性以「可定位的知識點、章節與題目」追蹤，不以讀完天數宣稱掌握全部 AI。核心涵蓋打造應用型 Agent 的主要責任；訓練、多模態與大規模平台另有後續安排。

| ID | 章節 | 知識點 | 深度 |
| --- | --- | --- | --- |
| C01 | [Agent 與 Harness 全貌](../chapters/foundations/01-agent-and-harness/README.md) | Agent, workflow, model, harness, runtime, environment, autonomy, acceptance | 核心正文＋六題 |
| C02 | [LLM 與 Context Engineering](../chapters/foundations/02-llm-and-context/README.md) | tokens, inference, instructions, structured outputs, context selection, compaction | 核心正文＋六題 |
| C03 | [工具契約與 Agent-Friendly 介面](../chapters/agent-core/03-tool-contracts/README.md) | function tools, schemas, validation, errors, authorization, idempotency, tool results | 核心正文＋六題 |
| C04 | [Agent Loop、規劃與停止](../chapters/agent-core/04-agent-loop-and-planning/README.md) | ReAct, plan-and-execute, routing, evaluator-optimizer, state machines, termination | 核心正文＋六題 |
| C05 | [Retrieval 與 RAG](../chapters/knowledge/05-retrieval-and-rag/README.md) | chunking, embeddings, lexical search, hybrid retrieval, reranking, grounding, freshness, ACL | 核心正文＋六題 |
| C06 | [Memory、State 與恢復](../chapters/knowledge/06-memory-and-state/README.md) | working memory, durable state, sessions, checkpoints, stores, retention, provenance | 核心正文＋六題 |
| C07 | [Codex Runtime 與訂閱入口](../chapters/codex-runtime/07-codex-runtime/README.md) | Codex CLI, exec, SDK, app-server, threads, turns, items, events, sandbox, approvals | 核心正文＋六題 |
| C08 | [訂閱 OAuth、Responses 與自建 Harness](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) | SIWC, OAuth, PKCE, scopes, Responses API, SSE, custom harness, tool loop, token lifecycle | 核心正文＋六題 |
| C09 | [MCP、Skills 與工具探索](../chapters/protocols/09-mcp-skills-and-discovery/README.md) | MCP host client server, capabilities, resources, prompts, tools, AGENTS.md, Skills, discovery | 核心正文＋六題 |
| C10 | [多 Agent、協調與 A2A](../chapters/protocols/10-multi-agent-and-a2a/README.md) | delegation, handoff, agent-as-tool, ownership, shared state, A2A, Agent Card | 核心正文＋六題 |
| C11 | [安全、信任邊界與人類控制](../chapters/production/11-safety-and-trust/README.md) | prompt injection, least privilege, approval, data exfiltration, supply chain, audit, sandbox | 核心正文＋六題 |
| C12 | [可靠性、冪等性與長任務恢復](../chapters/production/12-reliability-and-recovery/README.md) | timeouts, bounded retry, idempotency, cancellation, checkpoints, compensation, durable execution | 核心正文＋六題 |
| C13 | [Evals、Observability 與資源](../chapters/production/13-evals-observability-and-budgets/README.md) | tasks, trials, graders, outcome, trace, regression, calibration, latency, tokens, quotas | 核心正文＋六題 |
| C14 | [系統設計、案例整合與面試](../chapters/synthesis/14-system-design-and-interviews/README.md) | requirements, architecture, tradeoffs, data flow, rollout, SLOs, interviews, evidence | 核心正文＋六題 |

## 跨章主線

- **Harness engineering**：01 → 03 → 04 → 06 → 08 → 11 → 12 → 13。
- **Codex runtime**：07 → 08 → 09，並與 11–13 的強制控制與驗收對照。
- **面試系統設計**：所有章的 Q05 銜接 14，Q04／Q06 提供白板與交接稿。
- **2026 的時效點**：SIWC 訂閱推論、MCP 版本／擴充、A2A 1.0、Skills 按需載入、長任務 harness、Agent eval 與 agentic security。版本資訊集中在來源表，不埋在無日期的敘述中。

## 後續領域

多模態／computer use／語音、模型訓練與後訓練、進階資料與圖檢索、多租戶與分散式執行、自我改進治理。[第 15–28 天](../paths/further-study.md) 先安排問題與交付，再決定是否建立獨立 lab。

每個新增主題都要能回答：解決哪個問題、和哪個既有元件互動、失敗如何看見、用哪個題目驗證。
