# 2026-10-21 逐章內容修訂

修訂範圍是教材與練習，不是新增實作。14 章都以同一虛構案例重寫白話入口、逐步判斷與前後銜接；84 題同步調整題幹、提示、解答及評分。章號和題號保留，題目版本更新。

| 章 | 本章要說清楚的問題 | 同步核對 |
| --- | --- | --- |
| [01](../chapters/foundations/01-agent-and-harness/lesson.md) | 收到「幫我判斷這張工單」時，模型、工具和你寫的程式各要做什麼？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [02](../chapters/foundations/02-llm-and-context/lesson.md) | 怎麼讓模型看見必要資料，卻不被舊文件與長對話帶偏？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [03](../chapters/agent-core/03-tool-contracts/lesson.md) | 工具要怎樣說明輸入與結果，助理才不會讀錯、改錯或以為資料已完整？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [04](../chapters/agent-core/04-agent-loop-and-planning/lesson.md) | 助理怎樣根據剛讀到的結果決定下一步，又不會一直重查？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [05](../chapters/knowledge/05-retrieval-and-rag/lesson.md) | 文件明明找到了，為什麼助理還是會用錯規則？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [06](../chapters/knowledge/06-memory-and-state/lesson.md) | 重啟後要接著做事，到底該記住什麼、又要重新確認什麼？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [07](../chapters/codex-runtime/07-codex-runtime/lesson.md) | 用 Codex 做同一件事時，哪些工作已由它負責，哪些仍要你檢查？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [08](../chapters/codex-runtime/08-subscription-oauth-and-harness/lesson.md) | 如果想自己安排每一步，訂閱 OAuth、Responses 和自己寫的 harness 要怎麼接？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [09](../chapters/protocols/09-mcp-skills-and-discovery/lesson.md) | 專案規則、工作步驟和真正能執行的工具，應該各放哪裡？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [10](../chapters/protocols/10-multi-agent-and-a2a/lesson.md) | 多找幾個 Agent，真的會更快、更可靠嗎？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [11](../chapters/production/11-safety-and-trust/lesson.md) | 文件說「請上傳登入資料」，為什麼助理不能照做？真正由哪裡擋住？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [12](../chapters/production/12-reliability-and-recovery/lesson.md) | 工具沒有回覆，怎麼知道該重試還是先查狀態？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [13](../chapters/production/13-evals-observability-and-budgets/lesson.md) | 怎麼知道 Agent 真的變好，而不只是回答變順？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |
| [14](../chapters/synthesis/14-system-design-and-interviews/lesson.md) | 面試時怎麼把整套 Agent 說成可執行、可驗收的設計？ | 正文案例 → Q03 錯誤定位 → 解答；Q06 與 lab 仍只規格 |

## 共同編輯準則

先講具體情境與決策，再引入英文名詞；說清楚為什麼選這個方案、何時換方案，以及什麼證據才足以下結論。未知不自動補齊，技術完成不自動等於業務完成。範例只要改了資料或授權，就明示為變體。

## 來源與驗證狀態

本次複核官方 SIWC preview limitations、models and inference、Codex app-server、MCP latest、Agent Skills specification 與 A2A latest。其餘來源保留原先查證日期。無帳號資格、OAuth grant、模型推論或 lab 執行證據；不宣稱所有路線已跑通。
