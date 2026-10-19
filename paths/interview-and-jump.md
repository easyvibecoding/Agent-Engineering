# 面試與跳章路線

先選一條問題導向路線；章首先讀最小前置摘要，不必執行前章。卡在名詞時才補讀依賴章。

- **自建 harness 與訂閱推論**：[01](../chapters/foundations/01-agent-and-harness/README.md) → [03](../chapters/agent-core/03-tool-contracts/README.md) → [04](../chapters/agent-core/04-agent-loop-and-planning/README.md) → [06](../chapters/knowledge/06-memory-and-state/README.md) → [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) → [12](../chapters/production/12-reliability-and-recovery/README.md) → [13](../chapters/production/13-evals-observability-and-budgets/README.md)
- **Codex 整合與工具擴充**：[07](../chapters/codex-runtime/07-codex-runtime/README.md) → [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) → [09](../chapters/protocols/09-mcp-skills-and-discovery/README.md) → [11](../chapters/production/11-safety-and-trust/README.md) → [13](../chapters/production/13-evals-observability-and-budgets/README.md)
- **RAG／研究助理**：[02](../chapters/foundations/02-llm-and-context/README.md) → [05](../chapters/knowledge/05-retrieval-and-rag/README.md) → [06](../chapters/knowledge/06-memory-and-state/README.md) → [11](../chapters/production/11-safety-and-trust/README.md) → [13](../chapters/production/13-evals-observability-and-budgets/README.md) → [14](../chapters/synthesis/14-system-design-and-interviews/README.md)
- **可靠性與系統設計**：[03](../chapters/agent-core/03-tool-contracts/README.md) → [04](../chapters/agent-core/04-agent-loop-and-planning/README.md) → [06](../chapters/knowledge/06-memory-and-state/README.md) → [11](../chapters/production/11-safety-and-trust/README.md) → [12](../chapters/production/12-reliability-and-recovery/README.md) → [13](../chapters/production/13-evals-observability-and-budgets/README.md) → [14](../chapters/synthesis/14-system-design-and-interviews/README.md)
- **多 Agent 與協定面試**：[09](../chapters/protocols/09-mcp-skills-and-discovery/README.md) → [10](../chapters/protocols/10-multi-agent-and-a2a/README.md) → [11](../chapters/production/11-safety-and-trust/README.md) → [13](../chapters/production/13-evals-observability-and-budgets/README.md)

## 依題型跳題

Q01 測概念；Q02 測取捨；Q03 測除錯；Q04 測白板架構；Q05 練兩分鐘口答；Q06 將設計寫成可交接實作規格。[84 題索引](../maps/exercise-index.md)

## 三場模擬面試

1. 20 分鐘基礎：Agent／harness 分工、context、工具與停止。
2. 30 分鐘診斷：讀合成失敗軌跡，提出下一個觀測，而非直接猜修法。
3. 45 分鐘設計：研究、維護、工單三選一，討論權限、恢復、評估與發布。

每場由 Codex 一次問一題，最後依概念、取捨、失敗與驗證、表達各 0–2 分。分數作複習用途，保留具體錯題比追求滿分更有價值。

## 面試作品怎麼描述

可展示教材設計稿、案例圖與驗收規格；目前沒有 app 實作或部署。回答經驗時說明你實際觀察過什麼、只設計過什麼，以及下一步如何驗證。
