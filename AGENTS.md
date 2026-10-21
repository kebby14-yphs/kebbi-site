# 給 Claude 與 Manus 的更新指南

這個儲存庫是凱比開發進度網站：https://kebby14-yphs.github.io/kebbi-site/

一般進度與內容更新只改資料檔；新增網站功能時，才修改 `index.html` 與相關資料檔。推上 `main` 後網站會自動更新。

**每完成一件事（備份、修程式、測試結果、發現問題）就更新網站**，不要等老師問。

> ⚠️ 這是**公開**儲存庫，任何人都看得到。不要放密碼、token、電子郵件、電話、學生個資，也不要放電腦上的使用者路徑。程式碼放在私人儲存庫 `kebby14-yphs/kebbi-dev`。

## 要改哪個檔案

| 想做的事 | 檔案 |
|---|---|
| 更新某個目標的狀態 | `data/status.json` 的 `goals`，並更新 `updated` 日期 |
| 更新「下一步」清單 | `data/status.json` 的 `next` |
| 記錄一個新版本 | 在 `data/versions.json` **最前面**加一筆 |
| 新增分析筆記 | 在 `notes/` 加 `YYYY-MM-DD-主題.md`，並在 `notes/index.json` **最前面**加一筆 |
| 新增 / 修改比賽 | `competitions/YYYY-MM-DD-代號.json`，一場比賽一個檔（格式見下方）。老師也可以在網站「比賽專區」按「＋ 新增比賽」 |
| 原始檔清單 | `data/files.json`：只放檔名與私人儲存庫 `kebbi-dev` 裡的路徑，**檔案本身放 kebbi-dev，不要放進這個公開儲存庫** |
| 卑南語生活詞彙 | `data/vocabulary.json`：維持分類、卑南語詞彙、中文釋義與官方來源連結；新增或修訂詞條時沿用官方辭典拼寫並保留來源歸屬 |

### `status` 只能用這四個值

`done`（完成）、`doing`（進行中）、`blocked`（卡住）、`todo`（待辦）

### 版本紀錄格式

```json
{
  "version": "0.5",
  "date": "2026-10-20",
  "author": "Manus",
  "title": "一句話說明這版做了什麼",
  "changes": ["具體改變 1", "具體改變 2"]
}
```

- `author` 寫 `Claude`、`Manus` 或老師的名字
- 版本號：小改 +0.1；完成一個大目標（例如 SDK App 第一次成功說話）升到下一個整數

### 比賽格式

```json
{
  "name": "比賽名稱",
  "date": "2026-11-20",
  "organizer": "主辦單位",
  "location": "地點",
  "team": "隊伍 / 作品名稱",
  "status": "planning",
  "result": "成績（還沒比賽就留空）",
  "summary": "一句話摘要",
  "description": "詳細說明，可用 Markdown",
  "files_folders": ["卑南0930"],
  "links": [{ "title": "比賽簡章", "url": "https://..." }]
}
```

- `status`：`planning`（準備中）、`registered`（已報名）、`ongoing`（比賽中）、`done`（已結束）
- `files_folders`：對應 `data/files.json` 裡的 `folder`，網站會在比賽頁列出那些原始檔
- 不知道的欄位寫 `待補` 或留空，**不要猜**
- Google 雲端硬碟 / 文件連結要先拿掉 `ouid=`（帳號編號）和 `usp=` 參數再放上來
- 老師說「只當參考、不改網站」的資料，就不要加到網站
- 檔名只能用英數字、`-`、`_`、`.`

### 筆記檔名

只能用英數字、`-`、`_`、`.`，例如 `2026-10-20-sdk-tts-test.md`（網頁會拒絕其他檔名）。

## Commit 訊息

用一行說明，開頭標註是誰：

```
[Manus] 更新 SDK 下載狀態為完成
[Claude] 新增 v0.5 版本紀錄與 TTS 測試筆記
```

網站的「更新紀錄」分頁會直接顯示這些訊息，所以要寫得讓人看得懂。

## 改完之前先檢查

- JSON 格式正確（多一個或少一個逗號都會讓網頁載入失敗）
- 沒有放任何敏感資訊
- 如果另一方剛改過，先 `git pull` 再改，避免互相覆蓋

## 和 115kebby 專案同步

Claude 的 115kebby 專案可以把這個 GitHub 儲存庫加為專案知識，之後在專案裡按「同步」就會拿到最新內容。
