# 宜蘭市掃街地圖

宜蘭市徒步掃街的路線紀錄。地圖標有路名和地標，已經走過的街道用顏色標出來，並計算住宅區、商業區街道的覆蓋率。

## 兩個版本

| 版本 | 網址 | 可以做什麼 |
|---|---|---|
| 共用版（主要使用） | https://claude.ai/artifact/KBmtG4AephhbVw5SeRDjHH | 觀看、畫線、改備註、刪除；所有人即時同步。畫線需要登入 Claude 帳號。 |
| GitHub 唯讀版 | https://hanyingyilan.github.io/yilan-street-map/ | 只能觀看，不用登入。路線是 `routes.json` 裡的快照。 |

## 畫線方式（共用版）

1. 填日期、備註，選顏色，按「開始畫線」。
2. 在走過的路上依序點轉角或沿途的點，線會自動沿著馬路和巷弄連起來；按住拖曳也會貼著路走。
3. 雙擊或按「完成並儲存」結束。

## 檔案

- `index.html`：地圖網頁（內含街道與地標資料）。
- `routes.json`：已走路線的備份快照，GitHub 唯讀版從這裡讀取。

## 更新唯讀版的路線

共用版的路線不會自動同步到 GitHub。需要更新時，從共用版匯出最新路線，覆蓋 `routes.json` 後上傳即可。

道路與地標資料 © OpenStreetMap contributors（ODbL）。
