# 📁 FileVault — GitHub-Powered File Manager

A clean, self-hosted file manager that runs entirely as a static website on **GitHub Pages**. Upload, browse, download, and delete files — all stored directly in a GitHub repository via the GitHub REST API.

---

## ✨ Features

- **Upload** any file type (drag & drop or click to browse)
- **List** all files in your chosen folder with icon, size, and path
- **Download** files directly
- **Delete** files with confirmation
- **Search/filter** files by name
- **No backend** — pure static HTML + vanilla JS
- **Hosted free** on GitHub Pages
- **Auto-deploys** via GitHub Actions on every push

---

## 🚀 Setup Guide

### Step 1 — Create this repository

Create a **new public repository** on GitHub (e.g. `file-vault`) and push this code to it.

```bash
git init
git add .
git commit -m "Initial FileVault setup"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/file-vault.git
git push -u origin main
```

### Step 2 — Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. Save

The workflow in `.github/workflows/deploy.yml` will auto-deploy on every push to `main`.

### Step 3 — Create a Personal Access Token (PAT)

1. Go to [https://github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. Give it a name like `FileVault`
3. Select scopes: ✅ `repo` (full control of private repositories)
4. Click **Generate token** and copy it — you won't see it again

### Step 4 — Use the app

1. Visit your Pages URL: `https://YOUR_USERNAME.github.io/file-vault/`
2. Fill in the **Connect** form:
   - **GitHub Username**: `gouseshake0786`
   - **Repository Name**: `file-vault` (the repo where files will be stored — can be this same repo or a separate one)
   - **Branch**: `main`
   - **Personal Access Token**: paste the token from Step 3
   - **Storage Folder**: `uploads` (files go into this subfolder)
3. Click **Connect Repository** — credentials are stored in your browser's `localStorage` only

---

## 📂 Repository Structure

```
file-vault/
├── index.html                    ← The entire web app (single file)
├── .github/
│   └── workflows/
│       └── deploy.yml            ← GitHub Actions deployment workflow
├── uploads/                      ← Created automatically when first file is uploaded
│   └── your-files-go-here...
└── README.md
```

---

## 🔒 Security Notes

- Your **PAT is stored only in your browser's `localStorage`** — it never touches any server other than the GitHub API
- Use a **fine-grained PAT** with only the specific repo access if you want tighter control
- The GitHub API is called directly from your browser over HTTPS
- For a **private** files repo, keep the file storage repo private; the site repo can remain public
- Rotate your PAT regularly from [GitHub Settings → Tokens](https://github.com/settings/tokens)

---

## ⚙️ Configuration

All settings are editable via the **⚙ Settings** button after connecting. You can:
- Switch to a different repo or branch
- Update your PAT
- Change the upload folder path
- Disconnect (clears localStorage)

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Hosting | GitHub Pages |
| CI/CD | GitHub Actions |
| Storage | GitHub Repository (via REST API) |
| Frontend | Vanilla HTML / CSS / JavaScript |
| Auth | GitHub PAT (stored in localStorage) |

---

## 📝 License

MIT — use freely.
