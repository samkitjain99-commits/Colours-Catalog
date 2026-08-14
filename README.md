# Color Catalog Builder

A single-page, client-side color catalog app (primary/secondary colors, groups,
print sheets, WCAG contrast tools, backup/restore). No build step, no server —
just static HTML/CSS/JS with a Google Fonts `@import`.

## Files

- `index.html` — this is what Vercel actually serves at your site's root.
  **This is the file that matters for deployment.**
- `color-catalog-builder.html` — identical copy, kept under its original name
  for reference/local use.
- `vercel.json` — tells Vercel to skip framework auto-detection and treat
  this as a plain static site (no build step).

## Updating this repo

Whenever you get a new version of the app from Claude, just replace these
same four files (keeping the same filenames) and push:

```bash
git add .
git commit -m "Update app"
git push
```

Vercel will auto-redeploy within seconds since it's connected to this repo.

## Notes

- All data (catalog, groups, secondary color pool) lives in the browser's
  memory only — it resets on page reload. Use the **Backup & Restore** tab in
  the app to export/import a JSON snapshot if you want to persist data across
  sessions.
- The only external dependency is a Google Fonts stylesheet import (Playfair
  Display + Inter), loaded over HTTPS — no API keys or backend needed.
