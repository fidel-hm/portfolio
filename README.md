# Fidelis Müller — Portfolio

A desktop-first portfolio site built as plain static HTML/CSS (no build step) from
the Figma design spec in [`CLAUDE.md`](CLAUDE.md). Design tokens live in
[`tokens.css`](tokens.css) (1:1 from Figma); site-specific behaviour (project-menu
anchoring + responsive collapse) lives in [`site.css`](site.css). The three project
detail pages share one expressive "concept" template — styles in
[`concept.css`](concept.css), behaviour in [`concept.js`](concept.js) — but each
arranges its own media layout. Photos go in [`images/`](images/) (see its README).

## Pages

| File | Page |
|---|---|
| `index.html` | About (start page) |
| `projects.html` | Projects overview (hub + sidebar project menu) |
| `mono-poly.html` | Project 01 — mono / poly (2 verticals + 2 panoramas) |
| `inside-outside.html` | Project 02 — inside / outside (2 full-height images) |
| `showoff-understatement.html` | Project 03 — showoff / understatement (2 verticals) |
| `contact.html` | Contact (stub) |

## Run locally

It's just static files — open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Deploy

Hosted on GitHub Pages from the `main` branch (root). Push to `main` and Pages
redeploys automatically. The `.nojekyll` file disables Jekyll processing so all
files are served as-is.
