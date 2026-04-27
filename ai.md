---
title: AI Context for This Site
layout: base
---

# AI Context: Xanthan Portfolio Template

Paste this file into an AI assistant (Claude, ChatGPT, etc.) before asking for help with this site. It gives the AI the context it needs to make accurate, working edits.

---

## What This Is

This is a Jekyll static site built on the **Xanthan** framework, hosted on GitHub Pages. It uses Bootstrap for layout, Liquid for templating, and a CSS custom-property design system for all visual styling. No build tools, no JavaScript frameworks.

---

## File Map

| File / Folder | Purpose |
|---|---|
| `_config.yml` | Site title, author, URL, baseurl, analytics |
| `index.md` | Homepage — text intro + auto-generated card stack |
| `research.md`, `teaching.md`, `creative.md`, `cv.md` | Content pages |
| `_data/nav-top.yml` | Top navigation links (YAML list) |
| `_data/nav-profile.yml` | Sidebar photo, name, bio, social links |
| `assets/css/base.css` | All CSS variables — edit here to change colors/fonts |
| `assets/css/themes/` | Optional full theme overrides |
| `_includes/` | Reusable components (figure, jumbotron, etc.) |
| `_layouts/` | Page templates (`base`, `nav-profile`) |
| `docs/` | Full Xanthan documentation |

**Do not edit** files in `_layouts/`, `_includes/`, or `assets/js/` unless the user specifically asks to change framework behavior.

---

## Front Matter

Every `.md` page opens with a YAML block between `---` lines. Required fields:

```yaml
---
title: Page Title
layout: base          # or nav-profile (adds sidebar)
---
```

Fields that control the homepage card stack:

```yaml
homepage: true        # include this page as a card on the homepage
position: 2           # card order (lower = earlier)
summary: One or two sentences shown on the card.
thumbnail: assets/images/your-image.jpg
thumbnail-position: center   # CSS background-position (optional)
thumbnail-zoom: 1.2          # CSS background-size multiplier (optional)
```

---

## Navigation

`_data/nav-top.yml` — top navbar:

```yaml
- title: "Research"
  url: /research
- title: "Writing"
  url: /writing
```

`_data/nav-profile.yml` — sidebar (only on pages with `layout: nav-profile`):

```yaml
image_url: /assets/images/profile/photo.jpg
name: Your Name
description: One or two sentence bio.
links:
  - title: GitHub
    url: https://github.com/yourhandle
    icon: fab fa-github
```

Icon values use Font Awesome 5 class names (`fas fa-envelope`, `fab fa-twitter`, etc.).

---

## CSS Design System

All colors, fonts, and spacing are controlled by CSS custom properties in `assets/css/base.css`. **Never hardcode hex values in page content** — change the variables instead.

Key variables (in `:root`):

```css
/* Backgrounds */
--bg-page: var(--warm-white);
--bg-card: var(--warm-light);
--bg-nav: var(--sage);

/* Text */
--text-body: var(--sage-dark);
--text-h1: var(--golden-clay);
--text-h2: var(--sage);

/* Accents */
--accent-primary: var(--sage);
--accent-border: var(--golden-clay);

/* Fonts */
--font-heading: 'Inter', sans-serif;
--font-body: 'Source Sans 3', sans-serif;
--font-serif: 'Lora', serif;
```

Named palette colors (defined above the semantic variables):

```css
--sage: #6b8e7f;
--sage-dark: #2d3e35;
--golden-clay: #b8956a;
--warm-white: #f5f3f0;
--warm-light: #e8e4df;
--amber: #f59e0b;
```

To change the site's color scheme, reassign the semantic variables to new values in `:root` — or point them at new palette color names you define. Do not change the named palette colors directly; map semantic variables to them.

**Pre-built themes** in `assets/css/themes/` (e.g. `dark-energy.css`, `terra-cotta.css`) show the complete override pattern.

---

## Components (Liquid Includes)

Used inside `.md` files with `{% raw %}{% include ... %}{% endraw %}` syntax. Parameters are named with hyphens.
Review the _includes folder and see the references at https://xanthan-web.github.io/docs/reference/component-library for details.
---

## Layouts

- `layout: base` — full-width page, top navbar only
- `layout: nav-profile` — adds a sidebar driven by `_data/nav-profile.yml`; used on the homepage by default

---

## Image Paths

Images live in `assets/images/`. Reference them with a path relative to the site root:

```
assets/images/photo.jpg          ✓ correct
/assets/images/photo.jpg         ✓ also works
../assets/images/photo.jpg       ✗ don't use relative paths
```

---

## Adding and Removing Pages

**Add a page:**
1. Create `pagename.md` in the root folder with front matter (`title`, `layout`).
2. Add an entry to `_data/nav-top.yml`.
3. Add `homepage: true` + `summary` + `thumbnail` + `position` to make it appear on the homepage card stack.

**Remove a page:**
1. Delete the `.md` file.
2. Remove its entry from `_data/nav-top.yml`.

---

## ScrollStories

Scroll-driven narrative pages with parallax background images are available via the `scrollstory` layout and `_includes/scrollybox/` components. See `scrollstories/` for examples and `docs/scrollstories/` for documentation. This is an advanced feature — point the user to the docs rather than generating scrollstory code from scratch.
