# Color Catalog Builder

A single-page, client-side color catalog app (primary/secondary colors, groups,
print sheets, WCAG contrast tools, backup/restore). No build step, no server —
just static HTML/CSS/JS with a Google Fonts `@import`.

## Deploy to Vercel via GitHub

### 1. Create a GitHub repo
1. Go to [github.com/new](https://github.com/new) and create a new repository
   (public or private, doesn't matter).
2. Don't initialize it with a README/gitignore — you'll push these files as-is.

### 2. Push these files to the repo
From this folder, run:

```bash
git init
git add .
git commit -m "Initial commit: color catalog builder"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

(Replace `<your-username>/<your-repo>` with your actual GitHub path.)

### 3. Import into Vercel
1. Go to [vercel.com/new](https://vercel.com/new).
2. Click **Import Git Repository** and select the repo you just pushed.
3. Vercel should auto-detect it as **Other** (static site) since there's no
   `package.json` — leave Build Command and Output Directory blank/default.
4. Click **Deploy**. It'll be live at `<your-project>.vercel.app` within seconds.

That's it — no environment variables, no build step required.

## Files in this repo

- `index.html` — the entire app (this is what gets served at `/`)
- `vercel.json` — tells Vercel to skip framework auto-detection and treat this
  as a plain static site
- `README.md` — this file

## Notes

- All data (catalog, groups, secondary color pool) lives in the browser's
  memory only — it resets on page reload. Use the **Backup & Restore** tab in
  the app to export/import a JSON snapshot if you want to persist data across
  sessions or deployments.
- The only external dependency is a Google Fonts stylesheet import (Playfair
  Display + Inter), loaded over HTTPS — no API keys or backend needed.
