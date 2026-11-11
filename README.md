# Guitar Wiki

公開網站：https://tin9angugta.github.io/Guitar_Teach/
原始碼：https://github.com/Tin9AnGUgta/Guitar_Teach

TAICA 生成式 AI 第 9 堂 Agentic Work 作業：以可重複使用的 AGENTS.md 驅動吉他技巧百科的內容與網站開發。

## 本機執行
需要 Node.js 22 或更新版本，無第三方套件依賴。

```sh
npm run build
npm test
npm run dev
```

開啟 http://127.0.0.1:4173 。網站輸出在 dist/，請勿直接修改產物。

## 檔案結構
- AGENTS.md：AI 工作規則與驗收標準。
- content/lessons.json：四篇完整教學資料。
- templates/lesson.json：後續教學範本。
- scripts/build.mjs：產生首頁、文章、404 與資源。
- scripts/check.mjs：資料結構、連結與搜尋行為檢查。
- scripts/serve.mjs：本機 HTTP 預覽。
- scripts/extend.mjs：本次第四篇文章擴充實驗，一次性使用；重跑會阻止重複新增。
- assets/：共用 CSS 與 JavaScript。
- .github/workflows/pages.yml：main 分支更新時建置、測試及部署 Pages。
- docs/：測試報告與作業繳交摘要。

## 新增教學
先讀 AGENTS.md，再將 templates/lesson.json 的資料格式複製為 lessons.json 陣列中的新物件。填入唯一 slug 與完整內容，related 連至既有文章。執行 build、test、瀏覽器驗證，更新變更與測試紀錄。首頁卡片、文章與導覽會自動產生，不需修改生成器。

## GitHub Pages
此專案使用 GitHub Actions 部署 dist/，不是直接發布原始碼目錄。repository 的 Settings → Pages → Source 必須設為 GitHub Actions。公開發布須先取得專案擁有者確認。以實際 workflow 與網址驗證結果為準；目前部署狀態見 docs/SUBMISSION.md。

## 內容與素材
教學及短練習為本次專案自編；首頁吉他由 CSS 繪製，無外部圖片或字型。內容是學習練習建議，並非個別演奏能力的保證。疼痛時停止練習。

