# Color Catalog Builder — Netlify Deployment

A single-page, client-side color catalog app (primary/secondary colors, groups,
print sheets, WCAG contrast tools, backup/restore). No build step, no server —
just static HTML/CSS/JS with a Google Fonts `@import`.

There are two ways to deploy this to Netlify. Pick whichever is easier for you.

## Option A: Drag-and-drop (fastest, no GitHub needed)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag this whole folder (containing `index.html` and `netlify.toml`) onto
   the page.
3. Netlify uploads and deploys it immediately — you'll get a live URL like
   `random-name-123.netlify.app` within seconds.
4. Optional: click **"Site settings" → "Change site name"** to pick a custom
   subdomain, or add a custom domain later.

This method has no automatic redeploys — if you update the app later, you'll
need to drag the folder in again (or switch to Option B).

## Option B: Deploy via GitHub (recommended if you'll keep updating it)

### 1. Create a GitHub repo
1. Go to [github.com/new](https://github.com/new) and create a new repository.
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

### 3. Import into Netlify
1. Go to [app.netlify.com/start](https://app.netlify.com/start).
2. Choose **GitHub** and select the repo you just pushed.
3. Netlify reads `netlify.toml` automatically — **Build command** should be
   blank and **Publish directory** should be `.` (both already set in the
   config file, so you can usually just click through the defaults).
4. Click **Deploy site**. It'll be live at `<your-project>.netlify.app`
   within seconds, and every future `git push` will auto-redeploy it.

## Files in this folder

- `index.html` — the entire app (served at `/`)
- `netlify.toml` — tells Netlify there's no build step, just publish the
  folder as-is, plus a couple of harmless security headers
- `README.md` — this file

## Notes

- All data (catalog, groups, secondary color pool) lives in the browser's
  memory only — it resets on page reload, same as it would running locally.
  Deploying doesn't change this. Use the **Backup & Restore** tab in the app
  to export/import a JSON snapshot if you want to keep data across sessions.
- The only external dependency is a Google Fonts stylesheet import (Playfair
  Display + Inter), loaded over HTTPS — no API keys, no backend, no
  environment variables needed.
