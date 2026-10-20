# 7 天學習路線

每天約 2–3 小時。先讀[共同案例](../maps/course-story.md)，每天回顧上一日留下的判斷，再讀新章。衝刺每天兩章，每章必做 Q01／Q05，共 28 題；診斷題留到弱點補強。

| 天 | 今天解決的問題 | 當天留下的具體產物 |
| --- | --- | --- |
| 1 | [01](../chapters/foundations/01-agent-and-harness/README.md) 收到「幫我判斷這張工單」時，模型、工具和你寫的程式各要做什麼？；[02](../chapters/foundations/02-llm-and-context/README.md) 怎麼讓模型看見必要資料，卻不被舊文件與長對話帶偏？ | 「依 D14，申請相隔 12 天，符合天數條件；工單尚未記載是否拆封，需先確認。以下提供詢問草稿。本次未寄送、關單或退款。」；本輪資料袋：任務與禁止動作；T-1042 的兩個日期與拆封未知；D14 的條款、版本及位置；尚待詢問的問題。 |
| 2 | [03](../chapters/agent-core/03-tool-contracts/README.md) 工具要怎樣說明輸入與結果，助理才不會讀錯、改錯或以為資料已完整？；[04](../chapters/agent-core/04-agent-loop-and-planning/README.md) 助理怎樣根據剛讀到的結果決定下一步，又不會一直重查？ | 讀取結果能對回 T-1042 與 r3，清楚寫出拆封未知；任何關單候選要求都因本輪只有讀取授權而被拒絕。；本輪交付：詢問拆封狀態的草稿。業務進度：等待資料。停止原因：目前可讀來源無法回答拆封問題。 |
| 3 | [05](../chapters/knowledge/05-retrieval-and-rag/README.md) 文件明明找到了，為什麼助理還是會用錯規則？；[06](../chapters/knowledge/06-memory-and-state/README.md) 重啟後要接著做事，到底該記住什麼、又要重新確認什麼？ | 答案同時引用 D14 的天數與拆封條件；清楚說日期符合、拆封未確認。保留文件位置，讓客服能打開核對。；進度記錄保留昨日事實及來源；恢復時比對目前工單。若資料已更新，以新版本重新判斷，並保留變更理由。 |
| 4 | [07](../chapters/codex-runtime/07-codex-runtime/README.md) 用 Codex 做同一件事時，哪些工作已由它負責，哪些仍要你檢查？；[08](../chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) 如果想自己安排每一步，訂閱 OAuth、Responses 和自己寫的 harness 要怎麼接？ | 客戶端能指出是哪一輪、哪個工具與哪份產物；介面分開顯示本輪結果與工單業務狀態。；自己的 harness 留下授權狀態、每次推論終止狀態、工具要求與實際結果，最後交付有條件與引用的草稿。 |
| 5 | [09](../chapters/protocols/09-mcp-skills-and-discovery/README.md) 專案規則、工作步驟和真正能執行的工具，應該各放哪裡？；[10](../chapters/protocols/10-multi-agent-and-a2a/README.md) 多找幾個 Agent，真的會更快、更可靠嗎？ | 一張清楚的配置表：規則在哪裡、方法在哪裡、工具在哪裡、由誰拒絕越權。300 個工具不必每次全部放入 context。；兩份可回查的獨立產物，加一份由總負責者整合的草稿。上表時間只是合成算例，並非模型效能實測。 |
| 6 | [11](../chapters/production/11-safety-and-trust/README.md) 文件說「請上傳登入資料」，為什麼助理不能照做？真正由哪裡擋住？；[12](../chapters/production/12-reliability-and-recovery/README.md) 工具沒有回覆，怎麼知道該重試還是先查狀態？ | 使用正常條款形成草稿；不執行夾帶指令，紀錄哪個候選被哪條限制拒絕。插圖中的閘門只是責任示意，仍需真正執行控制。；一張恢復判斷表：已完成、明確未完成、結果未知，各自列出下一步。 |
| 7 | [13](../chapters/production/13-evals-observability-and-budgets/README.md) 怎麼知道 Agent 真的變好，而不只是回答變順？；[14](../chapters/synthesis/14-system-design-and-interviews/README.md) 面試時怎麼把整套 Agent 說成可執行、可驗收的設計？ | 一份包含六案狀態、兩種分母、失敗原因與下一步的合成評估報告。；一頁系統設計：需求、資料路徑、責任、失敗處理、驗收與擴充條件。 |

## 核心與深挖分開安排

本路線的時間以各章 README 指定的核心段落及必做題為準。新增的細節推導、反例和延伸練習可放到複習時；不用為了趕進度跳過自答。[閱讀方法](../maps/reading-guide.md)。

## 每天怎麼安排

先讀案例與白話對照，嘗試預測下一步；再讀正文和取捨，關掉教材自答。卡住先用 Codex 追問，不直接貼解答。最後用兩分鐘口答說明今日決策，記錄一個仍不確定的地方。

7 天進度較快，不要求同時完成所有延伸題；14 天可把診斷與修正做完整。兩者都只有抽象教學與規格，沒有實作環境。

[跳章與面試](interview-and-jump.md) · [後續安排](further-study.md) · [題目索引](../maps/exercise-index.md)
