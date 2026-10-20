# C08 · 題目

版本：2026-10-21。各題獨立，題號與 anchor 保留。14 天必做 Q01、Q03、Q05；7 天必做 Q01、Q05。先自答，卡住才看提示；個人答案放 .study/。

合成共同背景：T-1042 r3，2026-10-08 至 10-20 差 12 天。有效 D14 要求 ≤14 天且未拆封；r3 拆封未知。只有讀取與草稿授權，沒有寄送、關單、退款。題目中的 OAuth 與串流都是給定假資料，不是目前帳號狀態。

<a id="c08-q01"></a>

## C08-Q01 · 概念重建

某 app 已取得通過驗證的 ID token，但 token response 的 scopes 只有 openid、profile、email。使用者的原生 Codex 另外已登入。app 想讀 T-1042 並寫草稿。

1. 分別寫出 OAuth、Responses、harness 與工單工具的責任。
2. 現在能否送方案推論？缺的是哪個 granted scope？
3. 用兩個狀態欄位描述「登入」與「方案推論」，避免只用一個綠燈。

**交付與判分：**責任表、兩欄狀態；指出原生 Codex 登入不能代替此 app 的授權。

[提示](hints.md#c08-q01) · [參考解答](solutions.md#c08-q01)

<a id="c08-q02"></a>

## C08-Q02 · 方案比較

團隊有兩個目標：A 要看懂每一輪資料如何進出；B 要盡快設計客服操作台、顯示事件並接核准。兩者都使用同一 T-1042 假資料，尚未實作。

比較「自己取得合法授權後直接用 Responses 管 loop」與「自己的 app 接 Codex app-server」。各為 A、B 選一條路，列出 app 仍要管的三件事，以及改選另一條路的條件。

**交付與判分：**一張兩路比較表、一個切換條件；不能把 app-server 當成免 OAuth 或免驗收。

[提示](hints.md#c08-q02) · [參考解答](solutions.md#c08-q02)

<a id="c08-q03"></a>

## C08-Q03 · 軌跡診斷

合成請求 R3 的事件是：HTTP 200 → response.output_text.delta「可以…」→ response.failed，error.code=subscription_sharing_usage_limit_exceeded。先前已完成的讀工單工具記錄為 T-1042 r3、packaging=unknown，沒有寫入動作。服務未提供重設時間。

1. 把傳輸、推論、已知工具結果、客服交付各標一個狀態。
2. 寫出要保存的資料與給使用者的兩句說明。
3. 有人提議「每秒重試，或自動換 API key」；逐項判斷並說理由。

**交付與判分：**四層狀態、恢復紀錄、可對外說明；不補完片段、不猜重設時間或整體方案剩餘量。

[提示](hints.md#c08-q03) · [參考解答](solutions.md#c08-q03)

<a id="c08-q04"></a>

## C08-Q04 · 架構設計

請求 A 已 completed，輸出兩個完整工具要求：read_ticket(T-1042)，call_id=call_ticket_01；read_policy(D14)，call_id=call_policy_02。工具結果可能以相反順序回來。兩工具皆只讀；app 只有本題目標的讀取權。

畫出「推論完成 → 驗權 → 本機工具 → 配對結果 → 下一輪」；提供配對表及下一輪 input 的必要內容清單。再處理兩個變體：read_ticket 被拒絕；工具要求後推論 failed 而非 completed。

**交付與判分：**配對不依返回順序；兩變體各有停止／替代條件；指出最終草稿如何驗收。

[提示](hints.md#c08-q04) · [參考解答](solutions.md#c08-q04)

<a id="c08-q05"></a>

## C08-Q05 · 面試口答

面試官問：「用訂閱自己做 harness，和直接用 Codex，是不是同一件事？既然拿到 response.completed，為什麼還沒完成任務？」

先用 90 秒白話回答三條路的授權與 loop 責任，再用 T-1042 的一個具體工具往返說明。最後說出目前設計有什麼證據，還不能聲稱什麼。

**交付與判分：**先說責任，再用事件舉例；正確區分推論完成、工具完成、草稿完成與退貨資格。

[提示](hints.md#c08-q05) · [參考解答](solutions.md#c08-q05)

<a id="c08-q06"></a>

## C08-Q06 · 未來 Lab 規格

不執行 OAuth 或請求，只寫未來驗收矩陣。至少七類：拒絕同意、缺 scope、token 更新、串流斷線、工具拒絕、額度中止、正常完成。

每類包含合成輸入、預期 app 狀態、可否再推論／執行工具、保存證據、恢復條件。token 更新分直接 Responses 與 app-server env_key 兩種配置；額外加一列錯誤 call_id，說明怎樣避免把結果配錯。

**交付與判分：**至少八列、可客觀驗收的條件、未執行欄；不建立 app、依賴、憑證或環境。

[提示](hints.md#c08-q06) · [參考解答](solutions.md#c08-q06)
