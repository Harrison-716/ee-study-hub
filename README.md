# EE Study Hub｜電機學習知識庫

以 HTML、CSS、JavaScript 製作的靜態學習筆記網站。重點不只是完成單一頁面，而是透過 [AGENTS.md](./AGENTS.md) 設計可供 AI 重複使用的專案規則。

## 功能
- 電子學、電路學、線性代數、程式設計分類
- 搜尋標題、摘要與筆記內文
- 筆記詳細頁與可分享的 `#note/slug` 連結
- 響應式設計、深色模式及主題偏好記憶
- 資料與 UI 分離，可直接擴充筆記

## 本機執行
由於 JavaScript 使用 ES modules，請透過本機伺服器啟動：
```bash
python -m http.server 8000
```
瀏覽 http://localhost:8000/ 。

## GitHub Pages 部署
1. 在 GitHub 建立公開 Repository（例如 `ee-study-hub`）。
2. 將本專案所有檔案上傳至 Repository 根目錄。
3. 前往 **Settings → Pages → Build and deployment**，選 **Deploy from a branch**，Branch 選 `main`，資料夾選 `/(root)`，儲存。
4. 等候部署完成，網址通常為 `https://你的帳號.github.io/ee-study-hub/`。

## AI 擴充範例
將以下指令交給 AI：
> 請先閱讀 AGENTS.md，依照專案規範在 `content/notes.js` 新增「電路學：RL 電路暫態響應」，包含核心觀念、重要公式／方法與常見錯誤，並檢查搜尋、分類與詳細頁是否正常。

AI 不必重新設計版面，只需新增符合資料格式的物件，網站就會自動生成卡片、搜尋結果與詳細頁。新增功能時須遵守 AGENTS.md 的測試清單。

## 專案結構
```
index.html
AGENTS.md
README.md
assets/
  styles.css
  app.js
content/
  notes.js
```

## 注意
此專案為學習用途；內容採原創摘要及教學近似模型，實際解題仍應依題目指定條件判斷。
