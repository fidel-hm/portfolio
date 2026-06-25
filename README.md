# FidelMu Portfolio

A desktop-first portfolio site built as plain static HTML/CSS (no build step) from
the Figma design spec in [`CLAUDE.md`](CLAUDE.md). Design tokens live in
[`tokens.css`](tokens.css) (1:1 from Figma); the art-directed home wall and
responsive behaviour live in [`site.css`](site.css).

## Pages

| File | Page |
|---|---|
| `index.html` | Home — scattered project wall |
| `projects.html` | Projects overview |
| `mono-poly.html` | Project detail — mono / poly |
| `inside-outside.html` | Project detail — inside / outside |
| `personal-public.html` | Project detail — personal / public |
| `about.html` | About |
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
