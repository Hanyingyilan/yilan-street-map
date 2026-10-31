# 宜蘭市掃街地圖

宜蘭市徒步掃街的路線紀錄。地圖標有路名和地標，已經走過的街道用顏色標出來，並計算住宅區、商業區街道的覆蓋率。

## 網址

**https://hanyingyilan.github.io/yilan-street-map/**

打開就能看、畫線、改備註，不用登入；大家畫的線即時同步。刪除的路線會移到清單下方的「回收區」，可以還原。

路線存在 Firebase（專案 `yilan-street-map`，資料庫位置 asia-east1 台灣）。

## 畫線方式

1. 填日期、備註，選顏色，按「開始畫線」。
2. 在走過的路上依序點轉角或沿途的點，線會自動沿著馬路和巷弄連起來；按住拖曳也會貼著路走。
3. 雙擊或按「完成並儲存」結束。

## 檔案

- `index.html`：地圖網頁（內含街道與地標資料）。
- `routes.json`：2026-10-27 的路線備份（搬到 Firebase 前的資料）。

道路與地標資料 © OpenStreetMap contributors（ODbL）。

## 用打字新增路線（AI）

網頁把文字送到 Cloudflare Worker（`worker/worker.js`），Worker 呼叫 Claude 整理成步驟，網頁再畫到街道上，成為草稿，由隊員確認後才存入。

金鑰只放在 Worker 的環境變數，不會放進這個 repository：

| 名稱 | 種類 | 說明 |
|---|---|---|
| `ANTHROPIC_API_KEY` | Secret，必填 | Claude API 金鑰 |
| `TEAM_PASSWORD` | Secret，必填 | 團隊密碼 |
| `GOOGLE_MAPS_KEY` | Secret，選填 | 查店家位置（Places API）；沒有的話，網頁會請隊員在地圖上點 |
| `DAILY_LIMIT` | 變數，選填 | 每日次數上限，預設 30 |
| `USAGE` | KV 綁定，建議 | 記錄每日次數；沒綁定就不會限制次數 |

設定好後，把 Worker 網址寫進 `index.html` 開頭的 `window.ROUTE_AI_URL`，對話框才會出現。
