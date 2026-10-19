# 圖像教學與生圖紀錄

## 怎樣選圖

概念與比喻採 Codex 內建 imagegen；精確順序、狀態與依賴採可編輯 Mermaid。第一版穿插三張生圖，不為每章硬配一張裝飾圖。每章正文都有機制圖與完整案例。

圖放在概念案例附近，附 alt text、看圖重點與需要讀者回答的問題。顏色只是輔助，文字標籤仍要能辨認。圖說指出類比限制，不把插畫當安全、權限或真實執行證據。

## 產物與提示詞

工具：Codex 內建 imagegen，scientific-educational；生成日期：2026-10-19。未使用 CLI/API key fallback。保留章內資產與最終提示詞，原始生成檔留在 Codex 管理位置。

- [Agent 與 Harness 全貌概念圖](../chapters/foundations/01-agent-and-harness/assets/harness-overview.png) · [最終提示詞](../chapters/foundations/01-agent-and-harness/assets/prompt.md)
- [Memory、State 與恢復概念圖](../chapters/knowledge/06-memory-and-state/assets/context-and-state.png) · [最終提示詞](../chapters/knowledge/06-memory-and-state/assets/prompt.md)
- [安全、信任邊界與人類控制概念圖](../chapters/production/11-safety-and-trust/assets/trust-boundary.png) · [最終提示詞](../chapters/production/11-safety-and-trust/assets/prompt.md)

## 檢視與後續修訂

已逐張檢視標籤、角色與圖說：harness 圖並非固定串行機器；記憶櫃不代表模型權重或永久正確；信任閘門需真實執行控制實作。若變更流程，先改文字／Mermaid，再決定圖片是否需要修訂。

生成圖片是教材製作能力，不能據此推論自己的訂閱 Responses Agent 支援託管生圖。圖像原始檔隨教材一起保存於 repo，避免只存在本機私有路徑。
