# Gemini Live Web Console - Vercel 部署指南

## 部署到 Vercel（選項 2）

### 方法 A：透過 GitHub 直接部署（推薦）

#### 步驟 1：將程式碼放到您的 GitHub

```bash
# 在本機終端機執行：

# 1. 複製程式碼
git clone https://github.com/google-gemini/live-api-web-console.git
cd live-api-web-console

# 2. 建立新 repository（選擇其中一個方式）

# 方式 A：使用 GitHub CLI
gh auth login                    # 登入 GitHub
gh repo create gemini-live-voice --public --source=. --clone=false

# 方式 B：手動上傳
# 前往 https://github.com/new
# 建立新 repository，名稱為 gemini-live-voice
# 然後：
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/gemini-live-voice.git
git push -u origin main
```

#### 步驟 2：連接到 Vercel

1. 前往 [vercel.com](https://vercel.com)
2. 用 GitHub 帳戶登入
3. 點擊 **"New Project"**
4. 找到并選擇 `gemini-live-voice` repository
5. 點擊 **"Import"**
6. 設定專案：
   - **Project Name**: `gemini-live-voice`
   - **Framework Preset**: `Create React App`
   - **Build Command**: `npm run build` (預設)
   - **Output Directory**: `build` (預設)
7. 在 **"Environment Variables"** 新增：
   - `GEMINI_API_KEY` = `您的 API Key`
8. 點擊 **"Deploy"**

#### 步驟 3：完成 🎉

部署完成後，Vercel 會提供一個網址，例如：
```
https://gemini-live-voice.vercel.app
```

打開網址，輸入您的 API Key，即可使用！

---

### 方法 B：使用 Vercel CLI（需安裝）

```bash
# 1. 安裝 Vercel CLI
npm install -g vercel

# 2. 登入
vercel login

# 3. 進入專案目錄並部署
cd gemini-live-web-console
vercel --prod
```

依照指示設定即可。

---

## 常見問題

### Q：API Key 要去哪裡取得？
A：https://aistudio.google.com/app/apikey

### Q：部署後忘記 API Key 怎麼辦？
A：在 Vercel 專案設定中的 Environment Variables 新增或修改。

### Q：可以修改程式碼嗎？
A：可以！修改後 commit 並 push 到 GitHub，Vercel 會自動重新部署。

---

## 已完成的項目

- [x] 專案程式碼已準備好
- [x] Build 完成（build/ 目錄）
- [x] 依賴已安裝（node_modules/）

**注意**：由於此專案是 pure client-side，不需要後端伺服器！