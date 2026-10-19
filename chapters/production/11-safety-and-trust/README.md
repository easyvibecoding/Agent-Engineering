# 11 · 安全、信任邊界與人類控制

章節 ID：C11 · 查證基線：2026-10-19 · 核心路線：約 2–3 小時 · Lab：規格完成，尚未實作。

## 學習目標

- 能對 Agent 畫出資料與權限的信任邊界
- 能設計具體核准、拒絕與稽核方式

## 跳章入口

建議前置：[03 · 工具契約與 Agent-Friendly 介面](../../agent-core/03-tool-contracts/README.md)、[08 · 訂閱 OAuth、Responses 與自建 Harness](../../codex-runtime/08-subscription-oauth-and-harness/README.md)、[09 · MCP、Skills 與工具探索](../../protocols/09-mcp-skills-and-discovery/README.md)

最小前置摘要：外部資料能影響模型，但不能自行建立使用者授權；執行層必須獨立檢查。

先回答：本章最重要的執行責任由誰承擔？哪些結果需要外部證據？不熟悉的名詞可查[詞彙表](../../../maps/glossary.md)，再直接做題，不必先跑其他章的環境。

## 本章閱讀順序

1. [教學與完整案例](lesson.md)
2. [疑難與設計取捨](design-notes.md)
3. [題目與評分標準](exercises/README.md)：先自答 Q01、Q03、Q05
4. [分級提示](exercises/hints.md)：卡住才逐級讀
5. [參考解答](exercises/solutions.md)：自答或修正後再讀
6. [面試與追問](interview.md)、[Codex 協作卡](codex.md)
7. [未來 Lab 規格](lab/README.md)：本期不安裝或執行

## 時間安排

正文與圖解約 40 分鐘，官方來源重點閱讀 20–30 分鐘，必做題約 38 分鐘，Codex 追問約 20 分鐘，回想與錯題約 10 分鐘。延伸 Q02、Q04、Q06 不計入必做時間。

## 驗收自己的理解

不用參考解答解釋兩項學習目標；完成三題必做題並指出至少一項取捨、一種失敗與可查驗證據。遇到不確定處記錄待查，不以「讀過」當成理解完成。

[課程首頁](../../../README.md) · [14 天路線](../../../paths/14-days.md) · [題目索引](../../../maps/exercise-index.md) · [上一章](../../protocols/10-multi-agent-and-a2a/README.md) · [下一章](../12-reliability-and-recovery/README.md)
