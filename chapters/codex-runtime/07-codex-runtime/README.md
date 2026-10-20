# 07 · Codex Runtime 與訂閱入口

章節 ID：C07 · 內容修訂：2026-10-21 · 核心約 2–3 小時 · Lab 僅規格，尚未實作。

## 本章要留下什麼

用 T-1042 回答：**Codex 已幫我管哪些工作，哪些仍要自己驗收？** 留下入口選擇表、事件狀態表、責任邊界圖。能把「讀檔成功、草稿完成、工單處理完成」分開，就有可用的理解。

## 具體前置與跳章背景

知道模型可能提出工具要求，但工具的實際執行與授權由外部控制；知道保存的舊資料仍可能過期。陌生時回查[第 03 章工具契約](../../agent-core/03-tool-contracts/README.md)與[第 06 章狀態](../../knowledge/06-memory-and-state/README.md)，不要求完成 lab。

固定合成案例：T-1042 r3，日期差 12 天；D14 要求 ≤14 天且未拆封；拆封未知，只准讀取與草稿。完整設定見[共同案例](../../../maps/course-story.md)。本章不需要安裝 CLI、登入或取得 API key。

## 核心讀法：2–3 小時

1. [正文](lesson.md)：讀入口選擇、責任表、完整事件案例與反例，約 45 分鐘。
2. [設計取捨](design-notes.md)：比較薄入口與客戶端成本，約 20 分鐘。
3. [Q01、Q03、Q05](exercises/README.md)：先自答，約 40 分鐘；7 天路線先做 Q01、Q05。
4. 依需要開[提示](exercises/hints.md)，修正後才看[解答](exercises/solutions.md)，約 20 分鐘。
5. 用[面試追問](interview.md)口答，再用[Codex 協作卡](codex.md)追一個理解缺口，約 20 分鐘。

## 深挖讀法：另排 45–75 分鐘

比較 exec 點號事件與 app-server 斜線事件；讀正文官方來源的生命週期及核准段落，再做 Q02、Q04、Q06。畫出失敗、中斷、斷線三種分支，並說明哪些狀態需要讀回。不要用延伸閱讀拖住核心進度。

[未來 Lab 契約](lab/README.md)只定義輸入、觀察與驗收；不建立程式或環境。下一章將把自己取得推論授權、呼叫 Responses、自建 harness 三份責任再拆開。

[首頁](../../../README.md) · [上一章](../../knowledge/06-memory-and-state/README.md) · [下一章](../08-subscription-oauth-and-harness/README.md)
