# 2001 Toyota 4Runner Limited — Private Sale

One-page listing site. Pure static HTML/CSS, no build step, ready for GitHub Pages.

## Files

```
index.html       ← the listing page (Editorial '99 design)
images/          ← desktop-sized photos (max 2000px wide, ~80% JPEG)
images/mobile/   ← mobile-sized photos (max 900px wide, ~72% JPEG)
4runner pics/    ← original photos, untouched (NOT served — safe to leave or delete)
.claude/         ← local-preview helper config (not deployed)
```

## Deploy to GitHub Pages

1. Create a new public repository on GitHub (e.g. `4runner-for-sale`).
2. From this folder, push everything except `4runner pics/` (the originals — not needed for the live site):
   ```
   git init
   echo "4runner pics/" > .gitignore
   echo ".claude/" >> .gitignore
   git add .
   git commit -m "Initial listing"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages → Source: `Deploy from a branch` → Branch: `main` / `/ (root)` → Save.**
4. After ~1–2 minutes the site is live at `https://<your-username>.github.io/<repo-name>/`.

## Local preview

To preview the site locally with images rendering correctly:

```
cd "/Users/johndunlea/Documents/4runner sale/4runner-sale-website"
python3 -m http.server 8765 --bind 127.0.0.1
```

Then open http://127.0.0.1:8765/ in your browser.

## Page weight

| | Desktop | Mobile |
|---|---|---|
| index.html | ~19 KB | ~19 KB |
| Hero image | ~900 KB | ~170 KB |
| Full page first-load | ~1–2 MB | ~400 KB |
| Total `images/` directory | 19 MB | 3.4 MB |

GitHub Pages free-tier limits (verified from official docs):
- **Published site:** ≤ 1 GB → we're at ~22 MB ✓
- **Source repo:** soft 1 GB → ~22 MB if originals excluded ✓
- **Bandwidth:** 100 GB/month soft cap (≈ 250,000 mobile loads or 50,000 desktop loads/month) ✓
- **Builds:** 10/hour soft cap (we deploy on push — not an issue) ✓
- **Deploy timeout:** 10 min (no build step — instant) ✓

## Editing content

The page uses placeholder text marked `[placeholder]` for the sections you'll fill in later:
- Story / why-selling paragraphs
- Service log items (engine, suspension, brakes, cooling, tires, body)
- FAQ answers
- Carfax link target (the "View Carfax →" button currently points to `#`)
- VIN, prior owner count, location specifics

Search for `[placeholder]` in `index.html` to find them all.

## Contact

- Email: `jbdunlea@gmail.com`
- Phone: `929-277-0996`

## Notes

- Photos: originals kept in `4runner pics/`. The `images/` folder has rotated, renamed, web-optimized copies. Four photos that were stored sideways were rotated to display upright.
- Fonts: loaded from Google Fonts at runtime. First paint flashes briefly then swaps in the chosen typeface.
- No JavaScript — accordions in the FAQ use native `<details>` elements.
