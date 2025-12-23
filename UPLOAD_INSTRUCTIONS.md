# Heroic Flash Cards — GitHub Pages Upload (Split Build)

Your original `index.html` was ~100MB (too big for GitHub's 25MB-per-file web upload limit).  
This split build keeps everything functional on GitHub Pages by moving the big pieces into separate files:

- `assets/js/app.js` (≈23.6MB)
- `assets/music/*.mp3` (each < 12MB)
- `assets/css/styles.css`

## What to upload (repo root)

Upload these folders/files exactly as they are:

- `index.html`
- `assets/` (entire folder)
- `server/` (optional — only needed if you want to self-host LibreTranslate)

## Upload steps (GitHub website)

1. Download + unzip this package on your computer.
2. Open your repo on GitHub → click **Add file → Upload files**.
3. Drag-drop:
   - `index.html`
   - the whole `assets` folder (GitHub will keep folder structure)
   - (optional) `server` folder
4. Commit the changes.

Everything in this build is under **25MB per file**, so web upload works.

## GitHub Pages settings

Repo → **Settings → Pages**
- Source: **Deploy from a branch**
- Branch: `main` / folder: `/ (root)`

Wait for GitHub Pages to finish building, then open the site.

## LibreTranslate note (translation box)

This build defaults to using the public mirror:

- `https://libretranslate.de/translate`

If that mirror ever blocks requests or rate-limits:
- open the in-app settings and paste a different LibreTranslate endpoint, **or**
- run your own server using the `server/` folder (Docker compose + Caddy config included).
