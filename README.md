# Project Hub

A single-file, self-hosted landing page (Linktree-style) for the school consulting
deliverable **AI & Cloud-Powered Family Support Prototypes**.

Everything lives in **`index.html`** — no build, no dependencies, no `node_modules`.

## Edit content

Open `index.html` and edit the `SITE` object near the bottom (inside `<script>`):

- `title`, `subtitle`, `authors`, `eyebrow`, `footer` — text.
- `accent` — one hex color drives the whole theme.
- `cards` — each `{ icon, label, note, href }`. Icons: `play`, `code`, `doc`, `video`, `link`.

Replace the four `#TODO-*` hrefs with real URLs (live demo, GitHub repo, concept doc,
video/slides). A card whose href is still a `#TODO` renders as a muted **"Soon"** pill
instead of a dead link, so nothing broken ships by accident.

## Deploy

Same file, three ways:

- **GitHub Pages** — push this repo, then enable Pages on the default branch. `.nojekyll`
  makes Pages serve files verbatim.
- **Vercel** — import the repo; zero config (static, no framework).
- **Homeserver** — serve the folder with any static server:
  ```bash
  python3 -m http.server 8080
  # or: npx serve .   ·   nginx   ·   caddy file-server
  ```

You can also just double-click `index.html` to open it from `file://` — it works offline
(no CDN fonts, no external requests).

## Optional later

- Add an Open Graph image (`og:image`) for richer link previews.
