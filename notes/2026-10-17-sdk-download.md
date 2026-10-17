# NuwaSDK 下載失敗分析

**結論：**問題在 NUWA 的檔案伺服器或學校網路，不是帳號。換網路再試。

## 官方下載點

NUWA 開發者網站的下載彙整頁（`dss.nuwarobotics.com/gitbook/archive.html`）列出 Android SDK：

| 檔案 | 主機 | 結果 |
|---|---|---|
| `NuwaSDK-2021-07-08_1058_2.1.0.08_e21fe7.aar` | developer-docs.nuwarobotics.com | TCP 443 連線逾時 |
| 同上、`NuwaSDK-2020-09-23_0949_2.1.0.04_a77ee1.aar` | bj.bcebos.com（nuwarobotics-files） | TLS 握手失敗 |

電腦的 curl 和內建瀏覽器都失敗，所以不是單一程式的問題。

## 為什麼不用網路上別人的複本

GitHub 上可能有人放了同名的 .aar，但沒有官方校驗碼可以比對。SDK 會在凱比上以高權限執行，所以只用官方來源的檔案。

## 下一步

1. 換網路（手機熱點、家裡網路）下載上表第一個檔案
2. 不行的話寄信給 NUWA：service@nuwarobotics.com
3. 拿到後放進 `KebbiHello/app/libs/`，參考官方範例 `nuwarobotics/NuwaSDKExample` 的 `TTSActivity.java`
