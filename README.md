# github-sandbox

# 📥 Download Files via Commit Message (Release Mode)

A GitHub Actions workflow that lets you download files and publish them directly to **GitHub Releases** just by writing a special commit message — no terminal needed.

---  

## ⚙️ Setup
 
0. Fork this repo
1. Go to your repository on GitHub
2. Click **Settings** → **Actions** → **General**
3. Scroll down to **Workflow permissions**
4. Select **Read and write permissions** and click **Save**

> ✅ No PAT or secrets needed — the default `GITHUB_TOKEN` is enough for releases.

---

## 🚀 Usage

You trigger downloads by editing any file directly on GitHub and using a special commit message.

### How to trigger a download

1. Open any file in your repository (e.g. `README.md`)
2. Click the **✏️ Edit** button
3. Make a small change
4. Scroll to **Commit changes**
5. Select **Commit directly to `main`**
6. Enter one of the commands below in the commit message
7. Click **Commit changes**

---

## 📝 Commands

### 📦 Download files and upload to Release

```
download: URL1 URL2 URL3
```

**Example:**
```
download: https://example.com/file.zip
```

---

### 🗜️ Download and bundle into a ZIP (Release asset)

```
download-zip: URL1 URL2 URL3
```

**Example:**
```
download-zip: https://example.com/a.zip https://example.com/b.pdf
```

---

## 📦 Release Output

Each run creates (or updates) a release:

- Release name: `Auto Download`
- Tag: `auto-download`

| Command | Result |
|---|---|
| `download:` | Each file uploaded individually as a Release asset |
| `download-zip:` | A single `archive_YYYYMMDD_HHMMSS.zip` uploaded |

---

## 👀 Where to find files

1. Go to the **Releases** section of your repository
2. Open the latest release (`Auto Download`)
3. Download files from the **Assets** section

---

## ⚠️ Notes

- URLs must be public (no authentication)
- Separate URLs with spaces
- Workflow uses `[skip ci]` to prevent infinite loops
- If no valid command is found, workflow exits silently
- Existing assets with same name may be overwritten depending on implementation

---

## 💡 Tips

- Releases are better for large files compared to committing into the repo
- Keeps repository clean and avoids repo size limits
- Easier to download multiple files from one place
