# Agent Engineering 2026

客服傳來一張工單：「買了 12 天，能退嗎？幫我寫回覆。」

助理很快寫好：「可以，已處理。」你準備交出去，才發現它沒確認商品是否拆封。畫面上有答案，但你還不知道它真的讀了什麼、做了什麼。

這套課程從這個小問題開始，帶你逐步學會打造、檢查與解釋 AI Agent。用 **Codex runtime** 當現成執行系統，也拆開 **Agent harness** 看控制程式要負責什麼。案例全是合成教學。

適合會程式與 Git、想進入 Agent Engineering 的開發者。每天約 2–3 小時，可選 14 天、7 天或跳章；本期先學設計與面試表達，實作留到另行安排。

![Harness 的模型、工具、狀態、權限與驗收分工](chapters/foundations/01-agent-and-harness/assets/harness-overview.png)

## 從這裡開始

- [核心與深挖怎麼讀](maps/reading-guide.md)：先走完整案例，再按疑問補機制與反例。
- [14 天完整核心](paths/14-days.md)：每天一章，42 題必做。
- [7 天衝刺](paths/7-days.md)：每天兩章，28 題必做。
- [面試與跳章路線](paths/interview-and-jump.md)：依職能、題型或疑難直接開始。
- [84 題索引](maps/exercise-index.md)、[章內細節索引](maps/section-index.md)、[知識地圖](maps/knowledge-map.md)、[前置依賴圖](maps/dependencies.md)、[中英詞彙表](maps/glossary.md)。
- [第 15–28 天延伸安排](paths/further-study.md)。

## 目前交付與實作邊界

本版有 14 章正文、逐步案例與反例、設計取捨、84 題與分點判分、分級提示、參考解答、面試追問、Codex 協作卡、3 張 Codex 生圖與各章機制圖。**Lab 只有規格，尚未建立或執行實作。**

後續推論以訂閱為主：既有 Codex 原生登入，或應用程式自己的 Sign in with ChatGPT plan usage OAuth＋Responses。自己的應用需獨立授權、符合資格與 preview 能力；不把原生登入、模型清單或官方文件當成該 app 已跑通的證據。[路線與限制](references/subscription-runtime.md)

配圖使用 Codex 內建 imagegen 製作。這和自建 Agent 的 Responses 工具能力是兩條不同路徑，不能據此假設訂閱 preview 支援 hosted image generation。

## 章節

| 章 | 主題 | 你會碰到的問題 |
| --- | --- | --- |
| 01 | [Agent 與 Harness 全貌](chapters/foundations/01-agent-and-harness/README.md) | 助理說已處理，你能相信到哪一步？ |
| 02 | [LLM 與 Context Engineering](chapters/foundations/02-llm-and-context/README.md) | 資料給了一大包，為什麼還漏掉關鍵條件？ |
| 03 | [工具契約與 Agent-Friendly 介面](chapters/agent-core/03-tool-contracts/README.md) | 工具回 success，實際讀到了誰？ |
| 04 | [Agent Loop、規劃與停止](chapters/agent-core/04-agent-loop-and-planning/README.md) | 已經查第三次了，還要讓它繼續嗎？ |
| 05 | [Retrieval 與 RAG](chapters/knowledge/05-retrieval-and-rag/README.md) | 找到「14 天」，怎麼仍不能說一定可退？ |
| 06 | [Memory、State 與恢復](chapters/knowledge/06-memory-and-state/README.md) | 隔天重開，昨天的筆記還能直接信嗎？ |
| 07 | [Codex Runtime 與訂閱入口](chapters/codex-runtime/07-codex-runtime/README.md) | Codex 出現綠勾，究竟完成了什麼？ |
| 08 | [訂閱 OAuth、Responses 與自建 Harness](chapters/codex-runtime/08-subscription-oauth-and-harness/README.md) | 自己控制下一步，登入後還缺哪些工作？ |
| 09 | [MCP、Skills 與工具探索](chapters/protocols/09-mcp-skills-and-discovery/README.md) | 選單有 300 個工具，哪些真的能用？ |
| 10 | [多 Agent、協調與 A2A](chapters/protocols/10-multi-agent-and-a2a/README.md) | 多找兩個助理，怎麼反而花更多時間？ |
| 11 | [安全、信任邊界與人類控制](chapters/production/11-safety-and-trust/README.md) | 文件叫你上傳資料，這句話有權下令嗎？ |
| 12 | [可靠性、冪等性與長任務恢復](chapters/production/12-reliability-and-recovery/README.md) | 按了關單卻沒回覆，要不要再按一次？ |
| 13 | [Evals、Observability 與資源](chapters/production/13-evals-observability-and-budgets/README.md) | 報告寫 75%，到底算了哪些案例？ |
| 14 | [系統設計、案例整合與面試](chapters/synthesis/14-system-design-and-interviews/README.md) | 面試官問怎麼做，你的第一句話是什麼？ |

## 用同一個案例串起全部章節

從「一筆退貨工單要怎麼回覆」開始：先分清模型與執行系統，再處理資料、工具、狀態、權限、故障和評估。每章新增一種難度，也重述必要背景，方便跳章。[共同案例與全課進度](maps/course-story.md)寫清楚日期、店規、未知條件與各章變體。

正文先讓你遇到一個選擇，再帶你看資料、做判斷。名詞用到才解釋；長表和次要規格留在深挖。讀到停點可以留一張接讀卡，下次從原處繼續。每題仍有足夠資料、交付與判分依據。

## 每章怎麼讀

依序讀正文與圖說、設計取捨，先自答 Q01／Q03／Q05；卡住才讀分級提示，修正後再看參考解答。Q02／Q04／Q06 是延伸比較、設計與未來 lab 規格。

正文分核心與深挖閱讀；第一輪以案例和必做題為主，延伸推導按疑問補讀，不要求每天讀完所有材料。[閱讀方法](maps/reading-guide.md)。

每章都有最小前置摘要，可直接開始；建議前置是補讀導航，不要求先執行前章。個人答案可放 .study/，不會提交 Git。

## 為什麼這樣設計

- 通用概念先於產品名詞：能換 runtime，仍解釋責任與取捨。
- 把模型推論、工具執行、授權與完成驗收分開：容易診斷失敗與建立可測介面。
- 主題分類與獨立章節隔離：後續 lab 自帶環境、資料與驗收，不共用可變狀態。
- 題目、提示、解答分檔：支持先自答、逐步引導與模擬面試。
- 概念插畫配精確流程：先建立直覺，再核對狀態與邊界；圖片不當安全或執行證據。

## 時效、來源與證據

來源初次查證：2026-10-19；全章內容修訂：2026-10-21。訂閱 preview、MCP、Skills 與 A2A 的關鍵來源另於修訂日複核。[來源與更新政策](references/sources.md)、[視覺編排與生圖紀錄](references/visual-policy.md)、[驗收紀錄](references/verification.md)、[逐章修訂對照](references/editorial-review.md)。

核心知識地圖可追蹤與擴充；14 天目標是掌握核心設計及面試表達，延伸領域另有後續安排。合成教學案例清楚標示；設計、實作、測試與部署使用不同狀態。

## 授權

原創教材與本 repo 配圖採 [CC BY 4.0](LICENSE)。連結的第三方文件與論文仍依各自授權；本 repo 不重刊全文。
