# Project Hub

A single-file, self-hosted landing page (Linktree-style) for the school consulting
deliverable **AI & Cloud-Powered Family Support Prototypes**.

Hand-drawn "sketchnote" look: cream paper, marker headings, wobbly hand-drawn borders
(pure SVG filters), a hatched progress bar, and drawn "Soon" pills.

The page is **`index.html`** plus an **`assets/`** folder with two paper-texture
backgrounds. No build, no dependencies, no `node_modules`. The two handwriting fonts
(**Gochi Hand** + **Kalam**) are embedded as base64. It works **offline / from `file://`**
as long as `assets/` sits next to `index.html` (relative paths, no CDN, no external calls).

## Backgrounds

`assets/paper-mobile.jpg` (portrait) and `assets/paper-web.jpg` (landscape) are AI-generated
cream-paper photos with faint pencil doodles in the margins and a clean center for text.
CSS swaps them by width: mobile by default, `paper-web.jpg` at `min-width: 720px`. Drop in
your own images with the same names to reskin, or edit the `body::before` rule.

## Edit content

Open `index.html` and edit the `SITE` object near the bottom (inside `<script>`):

- `title`, `subtitle`, `authors`, `eyebrow`, `footer` — text.
- `accent` — one hex color drives the whole theme (star, byline dots, progress hatch, hovers).
- `progress` — `{ value: 0–100, label }`; the bar + number animate up on load.
- `cards` — each `{ icon, label, note, href }`. Icons: `play`, `code`, `doc`, `video`, `link`.

Fonts are set via the `--marker` (headings) and `--hand` (body) CSS variables in `:root`.
The "hand-drawn" wobble lives in the `#rough` / `#rough2` / `#roughLite` SVG filters — bump
their `scale` for messier lines, lower it for tidier ones.

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
(fonts embedded; backgrounds load from the local `assets/` folder; no CDN).

## Optional later

- Add an Open Graph image (`og:image`) for richer link previews.
