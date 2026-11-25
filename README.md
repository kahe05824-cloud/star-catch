# STAR CATCH｜星星收集（Vercel 版）

這是一個可直接部署到 Vercel 的靜態網站，使用 HTML、CSS、原生 JavaScript，不需要建置框架或資料庫。

## 專案檔案

- `index.html`：網站結構、遊戲畫面與分享／QR Code 頁面
- `style.css`：網站樣式與手機版排版
- `game.js`：遊戲規則、操作、音效、分數與 QR Code 產生功能
- `.gitignore`：排除本機環境檔、套件與 Vercel 暫存資料

## A. 建立 GitHub 公開專案

1. 登入 https://github.com/
2. 按右上角 `+` → `New repository`。
3. Repository name 建議輸入 `star-catch`。
4. 選 `Public`。不要勾選自動新增 README、License 或 .gitignore（本專案已包含 README 和 .gitignore）。
5. 按 `Create repository`。
6. 把本資料夾中的 `index.html`、`style.css`、`game.js`、`README.md`、`.gitignore` 上傳至 repository 根目錄。注意：不要把外層 ZIP 檔直接當成網站根目錄。
7. 如果使用 Git 命令列，請在解壓後的 `star-catch-site` 資料夾開啟 Terminal，執行以下命令。先將 GitHub 使用者名稱換成自己的：

   ```bash
   git init -b main
   git add .
   git status
   git commit -m "Build STAR CATCH game website"
   git remote add origin https://github.com/YOUR-GITHUB-USERNAME/star-catch.git
   git push -u origin main
   ```

   第一次推送時，Git 可能要求透過瀏覽器登入 GitHub。請使用你自己的帳號完成授權。若 Git 尚未設定姓名／Email，請依 GitHub 個人貢獻規範設定自己的 commit 身分；不要冒用他人身分。可使用 GitHub 提供的 noreply Email。

## B. 用 Vercel 匯入 GitHub 專案

1. 登入 https://vercel.com/ ，使用自己的帳號。
2. 若尚未連接 GitHub，先在 Vercel 授權 GitHub。
3. 在 Vercel Dashboard 按 `Add New` → `Project`（或 `New Project`）。
4. 在 Import Git Repository 清單中找到 `star-catch`，按 `Import`。
5. 設定如下：
   - Project Name：`star-catch`（或你喜歡的名稱）
   - Framework Preset：`Other`
   - Root Directory：`./`
   - Build Command：留空／不覆寫
   - Output Directory：`./`（若 Vercel 自動設為 `.`，保持預設即可）
   - Install Command：留空／預設
6. 按 `Deploy`，等待部署完成。
7. Vercel 會提供一個 `https://專案名稱.vercel.app` 網址。這就是可公開分享的正式網站網址。

這個專案只有 HTML/CSS/JavaScript，不需要 npm install 或 build。Vercel 官方說明：純靜態網站選 `Other`、不需要 build command，輸出目錄使用 `public`（若存在）或專案根目錄 `.`。參考：https://vercel.com/docs/builds

## C. 後續更新

把修改後的檔案存回 GitHub 的 `main` 分支。每次 push 到連接的 production branch，Vercel 會自動建立新的 production deployment，網站網址保持同一個 Vercel 專案網址。參考：https://vercel.com/docs/git

## D. 產生固定 QR Code

1. 開啟 Vercel 提供的正式 `vercel.app` 網址。
2. 在網站點「分享／QR Code」。
3. 貼上完整正式網址，按「產生 QR Code」。
4. 按「下載 QR Code PNG」，自行保存圖片。

QR Code 直接編入正式 Vercel 網址，不是限時短網址，不會隔天自動失效。只要 Vercel 專案及該網址持續有效，就可以繼續掃描。不要刪除專案或更換正式網域；若網址改變，需要重新產生 QR Code。

## E. 交件前驗收

- [ ] GitHub repository 設為 Public。
- [ ] repository 根目錄可看到 `index.html`、`style.css`、`game.js`。
- [ ] GitHub 有自己帳號的真實 commit／push 紀錄。
- [ ] Vercel 顯示 Deployment `Ready`。
- [ ] 用無痕視窗開啟 Vercel 網址，確認首頁正常。
- [ ] 實際測試鍵盤與手機拖曳操作。
- [ ] 測試漏接星星會結束、炸彈會結束、道具可用。
- [ ] 產生 QR Code 並用手機掃描，確認開到正式網址。
- [ ] 留存至少三項實際改善的前後畫面或 commit 證據。

## 功能與限制

- 電腦：使用鍵盤 ← → 或 A / D。
- 手機／平板：在遊戲畫面上左右拖曳。
- 漏接任何星星：立即結束。
- 碰到炸彈：立即結束（護盾道具可抵擋一次）。
- 藍色寶石：+5 分；護盾：短暫保護。
- 分數與排行榜存在各玩家自己的瀏覽器（localStorage），不是所有訪客共用的線上排行榜。
- QR Code 產生器使用 QRCode.js CDN，因此產生 QR Code 時需要網路連線。
- 網站字型使用 Google Fonts；若未連線，會自動退回系統字型。

## 安全提醒

老師的個人交件連結或個人金鑰不可放進公開 GitHub repository、程式碼、README、Vercel 環境變數或分享截圖。請只在老師指定的安全交件流程中使用個人金鑰。
