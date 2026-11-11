# Guitar Wiki — AI Agent 協作規約

## 目的與優先順序
為不同程度的繁體中文吉他學習者提供可操作、可驗收的技巧百科。此檔是所有後續 Agent 的起點。先閱讀此檔、README.md、content/lessons.json 與 templates/lesson.json，再修改網站。使用者當次指示優先；不得宣稱未完成的測試、上傳或部署已完成。

## 架構與技術
- 純 HTML、CSS、JavaScript；Node.js 內建模組產生靜態頁，不使用套件或 CDN。
- content/lessons.json：唯一文章資料來源；templates/lesson.json：新增內容範本。
- scripts/build.mjs：共享頁面模板與輸出；scripts/check.mjs：資料、連結及輸出驗收。
- assets/style.css、assets/app.js：共用樣式與互動；dist/：產物，不手改。
- docs/：測試與作業紀錄；.github/workflows/pages.yml：GitHub Pages CI。
- npm run build 產出 dist；npm test 驗收；npm run dev 在本機預覽。

## 設計規範
採深墨綠 #173e35、暖米白 #f6f3eb、銅橘 #b9512c，搭配深色正文與清楚留白。編輯誌風格，避免過度動畫。中文字使用系統字型，無外部字型依賴。內容寬度上限 1180px；文章正文上限 760px；手機 360px 起不得橫向溢出。正文至少 16px、行高 1.75。卡片顯示類別、難度、預估練習時間與摘要。使用語意標籤、唯一 h1、跳至正文連結、可見焦點與表單標籤；按鈕觸控區至少 44px。動態結果使用 aria-live；尊重 reduced-motion。

## 文章規格與模板
所有文章必須包含 slug、title、category、level、minutes、summary、prerequisites、goals、sections、routine、mistakes、checklist、related、updated。欄位形狀以 templates/lesson.json 為準。類別限定「基礎知識」「Fingerstyle」「進階技巧」「練習方法」；難度限定「入門」「中階」「進階」。minutes 是單次建議練習分鐘數，不是閱讀時間。

每篇至少三個具體教學段落、兩個學習目標、三個練習階段、兩項常見錯誤、三項可觀察驗收條件。段落應說明動作、聽覺判斷及下一步，避免只有定義。節拍器速度是起點建議，依乾淨度調整。明確區分音符、弦號、品格與左右手指法。標準調弦從第六弦到第一弦為 E–A–D–G–B–E；TAB 最上方為第一弦，0 為空弦。不得複製歌曲譜例或未授權圖片；自製短練習須標明。出現疼痛應停止，勿鼓勵忍痛或宣稱醫療療效。引用外部具體主張須實際查核並附原始來源，不虛構來源。一般自編練習標示原創，不假借專家背書。

## 命名與連結
slug 使用唯一小寫英文 kebab-case；檔名使用小寫英文。文章生成為 lessons/<slug>.html，標題可更新但已發布 slug 應保持穩定。所有資源使用相對路徑，支援 GitHub Pages /repository/ 子路徑；禁止硬編碼帳號或根目錄 /assets。related 必須指向既有 slug，不得自指。日期為 YYYY-MM-DD，僅在實質修訂時更新。不得把密碼、token、個資或本機絕對路徑寫入網站。

## AI 工作流程
1. 檢查 git status 與現有檔案，保留使用者改動；釐清任務及讀取上述規則。
2. 先複製文章範本，填入完整內容；只新增資料，不為單篇教學修改生成器。若 schema 改變，同步更新規約、範本、生成器及檢查。
3. 確認內容準確、原創、可練習；補上相關文章。一般實作自行決定；重大設計改動提出具體建議供確認。
4. 執行 npm run build 與 npm test。修正錯誤後重跑受影響的檢查。
5. 用 HTTP 伺服器驗證首頁、文章與 404；瀏覽器檢查桌面與手機、搜尋、分類、清空、無結果、鍵盤操作及列印。若工具無法完成，具體記錄未驗證項，不以程式檢查冒充視覺測試。
6. 更新 docs/TEST-REPORT.md、CHANGELOG.md 與必要的 README。紀錄測試證據、限制及變動檔案。
7. 發布前檢查 diff 與敏感資料。帳號授權及公開發布依平台及使用者要求取得確認，禁止刪除 repository、force push 或覆寫未知改動。
8. 發布後確認 workflow 成功與實際網址可用，才標記完成。失敗時保留錯誤證據、分析後修復；不要反覆建立 repository。

## 驗收與擴充測試
- 首版首頁與至少三篇完整教學；再依範本新增第四篇，記錄前後差異，新增文章不得需要修改生成器。
- build 與 test 成功，所有本機 href/src 均存在；related、slug、日期、必要欄位通過檢查。
- 搜尋與類別可交叉篩選，結果數與空狀態正確；無 JavaScript 仍可閱讀文章與導覽。
- 手機與桌面無溢出，鍵盤焦點可見，標題層級合理；不依顏色單獨傳達難度。
- GitHub repository、Pages URL、測試報告與作業摘要可供繳交。未完成項須如實標註。
