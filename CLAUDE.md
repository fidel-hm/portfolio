# FidelMu Portfolio — Design Spec

Design handoff for building this portfolio site as a prototype. Extracted directly
from Figma (file `vNpf36PUFegGWv0P5jliZZ`). **These values are the source of truth.**

> **For Claude Code:** the visual design below is fixed. You choose the tech stack
> (React/Vite, Astro, plain HTML/CSS, etc.) and adapt the *syntax*, but keep the
> exact colors, type sizes, spacing, and layout. All tokens and ready-made layout
> primitives live in **`tokens.css`** — import it or port it into your styling
> system (Tailwind config, CSS Modules, etc.).

The Figma is **desktop-only (1440px frame)**. Build desktop-first; responsive
behavior is not designed yet (see *Open questions* at the bottom).

> **Current build:** plain static HTML/CSS (no build step), deployed via GitHub
> Pages. Tokens live in `tokens.css` (1:1 from Figma); site-specific behaviour
> (project-menu anchoring + responsive collapse) lives in `site.css`.
>
> **Deviations from the Figma (intentional, per client):**
> - Header logo reads **"Fidelis Müller"** (Figma shows "FidelMu").
> - The **start page is About** (`index.html`). The Figma "Portfolio Home (1st)"
>   scattered project-wall was an early draft and has been dropped.
> - Projects are reached via the **Projects** nav → overview → sidebar menu.

---

## 1. Design tokens

| Token | Value | Used for |
|---|---|---|
| Background | `#f5f5f5` | page background |
| Text (primary) | `#000000` | body text, active nav/menu items, logo |
| Text (muted) | `#999999` | inactive nav/menu items, caption numbers, subtitles |
| Placeholder | `#d9d9d9` | image placeholder boxes |
| Divider | `#d9d9d9` | 1px vertical hairline |

**Font:** Inter (weights 400 Regular, 700 Bold) on every developed screen.

**Type scale**

| Role | Size | Weight | Line-height |
|---|---|---|---|
| Title (h1) | 40px | 700 | normal (~1.2) |
| Large / nav / sidebar / overview subtitle | 20px | 400 (logo 700) | normal |
| Body / captions / project subtitle | 16px | 400 | 24px (1.5) |

**Spacing** (8px base): `8 · 16 · 24 · 48 · 56 · 64`.

---

## 2. Global layout

- Centered frame, max width **1440px**.
- Horizontal page gutters: **120px** each side — content area **1200px**.
- Vertical page padding: **56px** top & bottom (developed pages).
- Vertical rhythm between major page sections (header → body): **64px**.

**Two-column body** (used by Overview, all Project pages, About):
`sidebar (280px) — gap 64px — 1px divider — gap 64px — main (fills remaining)`.

On the **About** page this is mirrored: the wide text **main** is on the left and
the narrow **image column** (280px) is on the right, divider between them.

---

## 3. Components

### Header (every page)
Full-width row, space-between, font-size 20px.
- **Logo** "FidelMu" — left, Bold, black.
- **Main Navigation** — right, horizontal, gap 24px: `Projects · About · Contact`.
  - Active link is **black**, inactive links are **muted `#999`**.
  - On project/overview pages "Projects" is the active (black) item.

### Project Menu (sidebar)
Vertical list, gap 24px, **vertically centered** in the body, font-size 20px:
`mono/poly · inside/outside · personal/public`.
- Active project is **black**, the others **muted `#999`**.

### Divider
1px wide, `#d9d9d9`, stretches the full height of the body row.

### Photo (single)
Full-width image placeholder, **height 560px**, `#d9d9d9`, with a caption row 16px
below (gap 16px).

### Photo pair
Two photos side-by-side, each `flex: 1`, gap 24px, image **height 480px** each,
caption below each.

### Caption
Space-between row, 16px: **label left** (black, e.g. "Untitled") · **index right**
(muted, e.g. "01").

### Project Teaser (home only)
Stacked: image placeholder on top, info row below (gap 24px). Info row is
space-between, 20px: **project title left · number right**.
> Note: standardized on **Inter** (Figma home teasers used Helvetica — see *Open questions*).

### About images
Right-hand 280px column with two stacked image placeholders, **height 420px** each,
gap 24px.

---

## 4. Pages

### Home — `index.html`
- Standard header.
- A **scattered / staggered "project wall"**: project teasers placed at **different
  sizes and offsets** (asymmetric, art-directed — *not* a uniform grid). In the
  reference: one ~285×300 top-left, one ~590-wide stepped down-right, one ~488-wide
  stepped further down-right. Reproduce the loose, diagonal cascade feel.

### Projects — Overview — `projects.html`
- Header (Projects active).
- Body = sidebar Project Menu (all muted, none selected) + divider + main:
  - **Title block** (gap 8px): `Kuration SoSe 26` (40px Bold) + `Christoph Noe`
    (20px Regular, black).
  - **Intro paragraph**, 16px, line-height 24px, full main width.
- Section gap in main: 48px.

### Project detail — `mono-poly.html`, `inside-outside.html`, `personal-public.html`
Same template, three instances (titles: "mono / poly", "inside / outside",
"personal / public").
- Header (Projects active) + sidebar Project Menu with the **current project active
  (black)**, others muted.
- Main column, section gap **56px**:
  1. **Intro**: title block (gap 24px) = headline 40px Bold + `SoSe 2026` (16px
     muted), then body paragraph 16px / line-height 24px, **max width 520px**.
  2. **Single photo** (560px tall) + caption `Untitled · 01`.
  3. **Photo pair** (two 480px-tall photos) + captions `Untitled · 02`, `Untitled · 03`.

### About — `about.html`
- Header (About active).
- **Mirrored** body: wide **main on the left** with `About` title (40px Bold) + body
  paragraph (16px / 24px, max width ~560px); **divider**; narrow **image column on
  the right** (280px) with two stacked placeholders (420px tall, gap 24px).

### Contact — `contact.html` — *stub*
Header-only placeholder — not yet designed in Figma, but the nav links to it.

---

## 5. Navigation map

| From | Link | Goes to |
|---|---|---|
| Logo | FidelMu | Home (`index.html`) |
| Nav | Projects | Projects — Overview |
| Nav | About | About |
| Nav | Contact | Contact stub (TODO design) |
| Sidebar menu | mono/poly | Project — mono/poly |
| Sidebar menu | inside/outside | Project — inside/outside |
| Sidebar menu | personal/public | Project — personal/public |
| Home | project teaser | corresponding project detail page |

---

## 6. Open questions / decisions to make

- **Font inconsistency:** the Figma home page uses **Helvetica**; every other
  screen uses **Inter**. This build standardizes on **Inter** everywhere.
- **Placeholder content:** all body copy is **Lorem ipsum** and all images are
  grey `#d9d9d9` boxes — wire up real content/images later.
- **Responsive:** only a 1440px desktop frame exists. This build collapses the
  two-column body to a single column below 900px and stacks the home "project
  wall" (see `site.css`).
- **Home wall layout:** the teaser positions are hand-placed; here approximated
  with absolute positioning on desktop, stacked on narrow screens.
