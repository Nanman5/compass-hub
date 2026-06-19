# Project Hub

A single-file, self-hosted landing page (Linktree-style) for the school consulting
deliverable **AI & Cloud-Powered Family Support Prototypes**.

Ships with **6 switchable theme variants** so you can pick the look you like:

1. **Daylight** — warm sunlit interior, light theme, serif, coral icon tiles
2. **Sunset** — centered hero, 4 icon tiles in a row, mountain dusk
3. **Clouds** — timeline list with dots + segmented progress, blue sky
4. **Sketch** — hand-drawn cream paper, marker fonts, wobbly SVG-filter borders
5. **Twilight** — minimal divider rows over a navy→sunset gradient
6. **Night** — glassy dark cards over a cozy laptop-at-dusk photo

Switch with the **1–6 pill at the bottom**, the arrow/number keys, or `index.html#v=3`
in the URL. The chosen variant is remembered in the URL hash. To lock one as the default,
set `setVariant(m ? +m[1] : 1, false)` at the end of the script to your number.

The page is **`index.html`** plus an **`assets/`** folder of background images. No build,
no dependencies, no `node_modules`. Fonts (**Playfair Display**, **Gochi Hand**, **Kalam**)
are embedded as base64. It works **offline / from `file://`** as long as `assets/` sits
next to `index.html` (relative paths, no CDN, no external calls).

## Backgrounds

`assets/bg-1.jpg`…`bg-6.jpg` (variant 4 uses `paper-mobile.jpg` / `paper-web.jpg`) are
AI-generated photos, each picked so the text area stays calm and readable. Each variant's
`--bg`, text colors, fonts and card style live in its `[data-variant="N"]` block in the
`<style>`. Drop in your own images with the same names to reskin.

## Edit content

Open `index.html` and edit the `SITE` object near the bottom (inside `<script>`):

- `title`, `subtitle`, `authors`, `eyebrow`, `footer` — text (shared across all variants).
- `progress` — `{ value: 0–100, label }`; the bar + number animate up on load.
- `cards` — each `{ icon, label, note, href }`. Icons: `play`, `code`, `doc`, `video`, `link`.

The accent color is `--accent` in `:root`. Variant 4's hand-drawn wobble lives in the
`#rough` / `#rough2` / `#roughLite` SVG filters — bump their `scale` for messier lines.

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
