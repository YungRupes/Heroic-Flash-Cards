# LibreTranslate API Server (for GitHub Pages / Static Sites)

This repo contains a **Dockerized LibreTranslate API** behind **Caddy (automatic HTTPS)** so you can use translation from a static website (GitHub Pages, Netlify, Vercel, etc.).

GitHub Pages is static hosting — it **cannot run LibreTranslate** itself — so you run this **server** somewhere else (a VPS, home server, etc.) and point your front-end to it.

## Folder layout

- `server/` — Docker Compose + Caddy reverse proxy (HTTPS + CORS)
- `.github/` — optional repo housekeeping

## Deploy (recommended)

**Requirements**
- A server with Docker + Docker Compose
- A domain/subdomain you control (example: `translate.yourdomain.com`) pointing to that server (DNS A/AAAA)

**Steps**
1. Clone this repo on your server
2. Edit `server/Caddyfile` and replace `translate.yourdomain.com` with your real subdomain
3. (Optional but recommended) Restrict CORS to your site origin (see `server/Caddyfile` comments)
4. Start:
   ```bash
   cd server
   docker compose up -d
   ```

Your API endpoint will be:
- `https://translate.yourdomain.com/translate`

## Local testing (no HTTPS)

Start only LibreTranslate:
```bash
cd server
docker compose up -d libretranslate
```

Then set your app’s endpoint to:
- `http://localhost:5000/translate`

> Note: open your website via `http://localhost` (not `file://`) during local testing so browser requests work normally.

## Notes

- Languages loaded are configured in `server/docker-compose.yml` via `LT_LOAD_ONLY`.
- The web UI is disabled (`LT_DISABLE_WEB_UI=true`) because this is meant to be an API for your app.
