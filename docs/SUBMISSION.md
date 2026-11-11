# TAICA 第 9 堂 Agentic Work 作業

## 專案與成果
名稱：Guitar Wiki 吉他技巧百科。目標：以 AGENTS.md 作為長期協作契約，讓後續 AI Agent 能沿用規則新增完整教材與網頁。

已建立首頁、基礎知識、Fingerstyle、進階技巧及練習方法四篇教學；支援搜尋與分類、文章目錄及相關教學。採 HTML、CSS、JavaScript，使用 Node.js 內建模組產生靜態頁。

## Agentic Work 流程
確認本機指定資料夾 → 先寫 AGENTS.md → 建立資料範本與共享生成器 → 開發首版三篇 → 執行檢查並修正問題 → 不更動生成器而新增第四篇 → 再次驗收 → 準備 GitHub Pages workflow。

規則涵蓋目的、架構、設計、內容品質、命名、AI 流程、授權與驗收；不是僅供本次使用的提示詞。文章與呈現分離，新增內容時沿用相同版型及自動檢查。

## 擴充實驗
新增文章：用 15 分鐘，建立有效練習循環。
新增方式：讀取 templates/lesson.json 格式後加入 content/lessons.json，透過既有生成器自動建立頁面。
驗收：由三篇／五頁／66 個本機連結，擴充至四篇／六頁／82 個本機連結，檢查皆成功。詳細證據與限制見 TEST-REPORT.md。

## 繳交連結與目前狀態
- AGENTS.md：專案根目錄。
- 原始碼：本機已完成，尚未上傳 GitHub。
- GitHub Repository：待建立與上傳。
- GitHub Pages 公開網址：待部署及實際驗證。
- 視覺驗證：受瀏覽器工具限制，尚未完成。

此文件為待部署的繳交草稿；取得實際 repository 與 Pages URL 後必須更新，不能以預測網址冒充完成。
