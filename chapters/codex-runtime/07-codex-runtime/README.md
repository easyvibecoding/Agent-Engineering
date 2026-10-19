# 07 · Codex Runtime 與訂閱入口

章節 ID：C07 · 查證基線：2026-10-19 · 核心路線：約 2–3 小時 · Lab：規格完成，尚未實作。

## 學習目標

- 能說明原生 Codex 與自訂客戶端的責任分界
- 能從事件與外部結果判斷任務狀態

## 跳章入口

建議前置：[01 · Agent 與 Harness 全貌](../../foundations/01-agent-and-harness/README.md)、[04 · Agent Loop、規劃與停止](../../agent-core/04-agent-loop-and-planning/README.md)、[06 · Memory、State 與恢復](../../knowledge/06-memory-and-state/README.md)

最小前置摘要：Harness 管執行循環；客戶端送任務與顯示結果；environment 承載檔案與程序。

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

[課程首頁](../../../README.md) · [14 天路線](../../../paths/14-days.md) · [題目索引](../../../maps/exercise-index.md) · [上一章](../../knowledge/06-memory-and-state/README.md) · [下一章](../08-subscription-oauth-and-harness/README.md)
