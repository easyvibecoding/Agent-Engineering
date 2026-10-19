# 訂閱、Responses 與 Harness 路線

查證基線：2026-10-19。原生登入、自己的 OAuth client 與平台 API key 是不同授權路徑。

| 路線 | 模型與執行責任 | 使用方式 |
| --- | --- | --- |
| 原生 Codex ChatGPT 登入 | Codex 提供現成 harness | 本機 CLI／exec 起步；SDK／app-server 視整合需求 |
| 自己 app 的 SIWC 訂閱授權＋Responses | app 自建 loop，或把 token 接到 Codex app-server | 適用官方文件描述的開源／本機託管場景，需獨立同意與資格 |
| 平台 API key | 依所選 runtime 自管或整合 | 概念比較；不作本期實作前提或自動 fallback |

## 自建 Harness 可以練的責任

Context 組合、候選工具呼叫驗證、本機工具與 MCP、歷史、checkpoint、核准、停止、取消、重試、恢復、事件與驗收都能在自己的執行系統設計。模型連線的限制不等於整個 harness 的全部能力。

## SIWC Preview 的必要條件

應用程式自己的註冊與使用者同意，檢查 granted scope 中的 chatgpt.tokens.use.direct；原生 Codex 已登入不證明自己的 app 已授權。使用公開 POST https://api.openai.com/v1/responses，以符合授權的 access token 作 Bearer。

HTTP 要求 store=false、stream=true，input 帶必要歷史，省略 previous_response_id。不能照抄一般 API 所有欄位；temperature、max_output_tokens、conversation 等在此 preview 不支援。模型依所選帳號清單與實際推論確認。

Function/custom tools 的封裝依目前文件使用 namespaces 或 additional_tools；hosted file search、Code Interpreter、原生 computer use、hosted MCP/connectors、image generation、Responses tool_search 等目前不在此路線支援範圍。本機工具與其控制機制由 app 或 Codex harness 提供，是另一層責任。

## 狀態與完成

store=false 不禁止 app 保存經授權的本機歷史。Responses 串流須讀到 response.completed 才算該次推論成功；failed、incomplete、斷線與額度錯誤分開。推論成功之後，仍需驗收任務產物。

額度不足或政策拒絕先保存狀態並停止，不自動切換計費，不推定整個訂閱用完或重設時間。此 repo 尚未實際建立 OAuth client 或執行推論。

## 教材生圖

章節圖片由 Codex 內建 imagegen 產生，屬教材製作；沒有用 API key fallback。它不構成 SIWC Responses preview 支援 hosted image generation 的證據。

官方來源：[Overview](https://developers.openai.com/siwc/token-sharing-open-source)、[Sign-in](https://developers.openai.com/siwc/token-sharing-open-source/sign-in)、[Inference](https://developers.openai.com/siwc/token-sharing-open-source/models-and-inference)、[Preview](https://developers.openai.com/siwc/token-sharing-open-source/preview-limitations)、[Errors](https://developers.openai.com/siwc/token-sharing-open-source/errors-and-recovery)。
