# 測試報告

日期：2026-11-11。環境：Windows、本機 Node.js v26.13.0；GitHub Actions Ubuntu／Node.js v22.23.4。

## GitHub 遠端驗收
已將專案上傳至 https://github.com/Tin9AnGUgta/Guitar_Teach ，commit af959da26254eb85854df98fd926e428007c81d7。
Run 43006575544 的 npm run build 與 npm test 皆成功，檢查結果同本機。configure-pages@v5 回報 Get Pages site failed / Not Found，表示需要在 Settings → Pages 將 Source 設為 GitHub Actions。deploy job 因此前置失敗而跳過；公開部署尚未完成。

## 已執行
1. node scripts/build.mjs：成功產生首頁、四篇文章、404 與共用資源。
2. node scripts/check.mjs：PASS: 4 lessons, 6 HTML pages, 82 local links; search/category/empty/reset behavior。
3. 首版曾以三篇資料驗收成功：3 lessons, 5 HTML pages, 66 local links。
4. 擴充實驗使用 scripts/extend.mjs 讀取既有範本新增第四篇，未修改 build.mjs。第四篇自動出現在首頁並產生文章、相關連結。
5. 檢查涵蓋必要欄位、slug 唯一性、類別與難度、練習段落數、related 有效性、每頁唯一 h1、語系與 viewport、本機資源及錨點。
6. 使用 production app.js 的 DOM 模擬驗證搜尋、分類交叉篩選、無結果、清除與焦點回復。這是程式行為測試，不代表真實瀏覽器驗證。

## 已修正問題
- 初版 related 指向尚不存在的第四篇，改為既有教學後通過。
- 修正相關文章自指。
- PowerShell UTF-8 BOM 造成 JSON.parse 失敗，轉回無 BOM UTF-8。

## 尚未驗證
再次測試 HTTP：首頁 / 為 200、/lessons/fingerstyle-pattern.html 為 200、/missing.html 為 404，皆回傳 Guitar Wiki 頁面。GitHub 連接器可讀取帳號及 repository 清單，但未提供建立 repository 或啟用 Pages 的工具；瀏覽器重試仍回報 browser access host unavailable。

瀏覽器工具先回報 browser access host unavailable，後因無法可靠識別 Windows 目前瀏覽器網址而停止。桌面及手機視覺、實際鍵盤操作、列印、真實瀏覽器 console 尚未驗證。GitHub Actions 執行與公開 Pages 網址尚未驗證。不得把上述自動檢查視為這些項目的完成證據。
