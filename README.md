# PeakEdge Digital — public website only

This folder is the **entire** static site. Nothing else from the parent project belongs on GitHub if you only want the webpage live.

## Files here

- `index.html` — homepage  
- `css/style.css` — styles  
- `assets/favicon.svg` — favicon  
- `.nojekyll` — tells GitHub Pages not to use Jekyll  

## GitHub Pages (website-only repo)

**If `publish-site` lives inside a bigger Git project** (e.g. the Digital AI Assets monorepo), avoid `git init` *inside* that subfolder — it creates a nested repo mess. Instead copy this folder to a clean location:

```bash
cp -R "/path/to/Digital AI Assets/publish-site" ~/peakedge-site-github
cd ~/peakedge-site-github
git init
```

1. Create a **new** empty repository on GitHub (e.g. `peakedge-digital-site`).
2. In Terminal (from the **clean** copy, or from `publish-site` only if it is **not** inside another git repo):

```bash
git add .
git commit -m "PeakEdge Digital marketing site"
git branch -M main
git remote add origin https://github.com/YOUR_USER/YOUR_REPO.git
git push -u origin main
```

3. GitHub → **Settings → Pages** → Source: branch **main**, folder **`/ (root)`** → Save.
4. Site URL: `https://YOUR_USER.github.io/YOUR_REPO/`

## Sync from `docs/` after you edit the site

When you change files under `docs/` in the main project, copy them here:

```bash
cd "/path/to/Digital AI Assets"
./scripts/sync_publish_site.sh
```

Then inside `publish-site/`: `git add -A && git commit -m "Update site" && git push`
