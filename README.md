# Fidelis Müller — Portfolio

A desktop-first portfolio site built as plain static HTML/CSS (no build step) from
the Figma design spec in [`CLAUDE.md`](CLAUDE.md). Design tokens live in
[`tokens.css`](tokens.css) (1:1 from Figma); site-specific behaviour (project-menu
anchoring + responsive collapse) lives in [`site.css`](site.css).

## Pages

| File | Page |
|---|---|
| `index.html` | About (start page) |
| `projects.html` | Projects overview |
| `mono-poly.html` | Project detail — mono / poly |
| `inside-outside.html` | Project detail — inside / outside |
| `personal-public.html` | Project detail — personal / public |
| `motion-still.html` | Project detail — motion / still (dynamic/playful design direction; styles in `concept.css`) |
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
