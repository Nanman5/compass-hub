# Project Hub

A single-page, self-hosted landing page (Linktree-style) for the school consulting
deliverable **AI & Cloud-Powered Family Support Prototypes** — by Katlyn V., Shondalle C.
& Hernan L. (Dr. Walker's Family Life Class).

Hand-drawn "sketchnote" look: a real cream-paper photo with margin doodles, marker
headings, wobbly hand-drawn card borders (pure SVG filters), a hatched progress bar, and
drawn "Soon" pills.

## Files

- `index.html` — the whole page (markup + styles + the `SITE` config). Fonts
  (**Gochi Hand** + **Kalam**) are embedded as base64.
- `assets/paper-mobile.jpg` / `assets/paper-web.jpg` — paper backgrounds (CSS swaps them at
  `min-width: 720px`).
- `assets/concept-brief.pdf` — the concept brief the "Concept Doc" card links to.

No build, no dependencies, no `node_modules`. Works **offline / from `file://`** as long as
`assets/` sits next to `index.html`.

## Edit content

Open `index.html` and edit the `SITE` object near the bottom (inside `<script>`):

- `title`, `subtitle`, `authors`, `eyebrow`, `footer` — text.
- `progress` — `{ value: 0–100, label }`; the bar + number animate up on load.
- `todo` — `{ label, items: [...] }`; a hand-drawn "Still to do" checklist of remaining work.
- `cards` — each `{ icon, label, note, href }`. Icons: `play`, `code`, `doc`, `video`, `link`.

Cards whose `href` still starts with `#TODO` render a muted **"Soon"** pill instead of a dead
link. Currently live: **Live Demo**, **GitHub Repo** and **Concept Doc**. Still to fill in:
**Video & Slides**.

The accent color is `--accent` in `:root`. The hand-drawn wobble lives in the
`#rough` / `#rough2` / `#roughLite` SVG filters — bump their `scale` for messier lines.

## Deploy

Published via **GitHub Pages** from the `master` branch (`.nojekyll` serves files verbatim).
Also deployable on Vercel (zero config) or any static server
(`python3 -m http.server`, nginx, caddy).
