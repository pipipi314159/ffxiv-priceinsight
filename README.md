# FFXIV Price Insight（台服繁中版）

[Price Insight](https://github.com/kouzukii/ffxiv-priceinsight) 移植到《Final Fantasy XIV》台灣版（繁體中文）客戶端的版本。

滑鼠移到物品上時，會在物品說明框底部顯示 [Universalis](https://universalis.app/) 的交易板 NQ/HQ 最低價與最近成交價。

![preview](images/image1.png)

## 版本資訊

| 項目 | 內容 |
|---|---|
| 原版 | [kouzukii/ffxiv-priceinsight](https://github.com/kouzukii/ffxiv-priceinsight) |
| 基於版本 | 2.11.3.0（原 repo 無 tag，使用 commit `3c1c16d756859395b58f583f97e251135bbccda8`，2025-08-07「Update for Dalamud 13 and FFXIV 7.3」） |
| Dalamud API | API13（Dalamud.NET.Sdk 13.0.0） |
| 分支 | `tw-api13` |
| 程式修改 | 無（僅修改插件名稱、repo 網址與本說明文件） |

## 台服已確認功能

- 插件可正常載入（物品說明框的兩個特徵碼在台服可用）
- 滑過物品時顯示價格（原始伺服器 / 陸行鳥資料中心其他伺服器的最低價、資料更新時間）
- 堆疊物品的價格顯示
- 按住 Alt 重新抓取價格
- `/priceinsight` 開啟設定視窗

## 注意事項

- 價格資料來自 Universalis，台服陸行鳥資料中心（伊弗利特、迦樓羅、利維坦、鳳凰、奧汀、巴哈姆特、拉姆、泰坦）有資料，但更新頻率取決於有安裝上傳插件的玩家數量。
- 設定中的「Region」選項在台服意義不大（只有一個資料中心），開啟後地區名稱會顯示為 `unknown`，不影響價格。
- 預設查詢**原始伺服器**的價格；跨服時若要看當地伺服器價格，請在設定中勾選「Current World」。
- 偶爾出現 `Failed to retrieve data from Universalis` 的錯誤屬於網路暫時中斷，再滑過一次或按 Alt 即可。
- 使用前請停用官方版 Price Insight，避免衝突。

## 編譯方式

需安裝 .NET SDK 與台服 Dalamud（設定 `DALAMUD_HOME` 指向 Dalamud Injector 資料夾）：

```bat
git checkout tw-api13
set DALAMUD_HOME=<你的 Dalamud Injector 資料夾>
dotnet build PriceInsight.csproj -c Release
```

輸出位於 `bin\Release\PriceInsight.dll`，可在 `/xlsettings` → 實驗性功能 → 開發插件位置中加入此路徑載入。

## 原作者與授權

- 原作者：[Kouzukii](https://github.com/kouzukii)
- 授權：MIT License（見 [LICENSE](LICENSE)）

本版本的問題請回報到[本 repo 的 Issues](https://github.com/pipipi314159/ffxiv-priceinsight/issues)，**請勿回報給原作者**。
