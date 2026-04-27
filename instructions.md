---
title: Getting Started with Your Portfolio
layout: base
---

# Getting Started with Your Portfolio

> **When you're done setting up your site, delete this file and remove the "Instructions" entry from `_data/nav-top.yml`.** It's only here to help you get started.

This template gives you five content pages, a sidebar profile, and Xanthan's full component library. Work through the steps below in order — most users are done in under an hour.

## What You Have

- **Homepage** (`index.md`) — your introduction, with cards linking to other pages
- **Research** (`research.md`) — scholarly interests, projects, publications
- **Teaching** (`teaching.md`) — teaching philosophy, courses, student work
- **Creative** (`creative.md`) — a flexible fourth page; rename and repurpose as needed
- **CV** (`cv.md`) — your curriculum vitae in Markdown
- **Sidebar** (`_data/nav-profile.yml`) — your photo, name, bio, and social links
- **Docs** (`docs/`) — full Xanthan documentation bundled with your template


## Step 1: Open the Editor

The easiest way to edit your site is GitHub's built-in editor:

1. Go to your repository on GitHub
2. Press the **`.` (period) key** — VS Code opens in your browser
3. All your files are in the left sidebar; click any file to edit it
4. **Save:** `Ctrl+S` (Windows/Linux) or `Cmd+S` (Mac)

You can also clone the repo and edit locally if you prefer.


## Step 2: Update `_config.yml`

Open `_config.yml` and fill in the required fields:

```yaml
title: Your Name
author: Your Name
description: Academic portfolio and digital research
url: "https://yourusername.github.io"
baseurl: "portfolio-template"
```

- `url`: your full GitHub Pages URL (e.g. `https://yourusername.github.io`)
- `baseurl`: We need to use `portfolio-template` for our demo website, but you probably want to set this as empty (`""`) so that your ULR will be `yourusername.github.io` instead of `yourusername.github.io/portfolio-template`.



## Step 3: Update Your Homepage (`index.md`)

Open `index.md` and replace the placeholder name and bio paragraph with your own. The card links at the bottom are generated automatically — leave that code in place.


## Step 4: Set Up Your Sidebar (`_data/nav-profile.yml`)

Open `_data/nav-profile.yml` and update:
- `image_url` — path to your photo (put it in `assets/images/profile/`)
- `name` — your name
- `description` — one or two sentences about you
- `links` — your website, email, GitHub, etc.

**Don't want a sidebar?** The sidebar only appears on pages using `layout: nav-profile`. Your homepage uses it by default; all other pages use `layout: base` (no sidebar). If you'd prefer a plain full-width homepage too, open `index.md` and change `layout: nav-profile` to `layout: base`.


## Step 5: Edit Your Content Pages

Open each page and replace the placeholder content with your own. Each page has inline guidance at the top explaining what to change.

- `research.md` — overview of your scholarly work and projects
- `teaching.md` — teaching philosophy, courses, sample student work
- `creative.md` — rename and repurpose this page for whatever doesn't fit elsewhere
- `cv.md` — your full CV; see the note on that page about using AI to convert a Word doc

To remove a page from your site: delete the file and remove its entry from `_data/nav-top.yml`.


## Step 6: Add New Pages (optional)

To add a page like "Blog" or "Writing":

1. Create a new file in the root folder (e.g., `writing.md`)
2. Add this front matter at the top:

```yaml
---
title: Writing
layout: base
homepage: true
position: 5
summary: Essays and public writing.
thumbnail: assets/images/your-image.jpg
---
```

3. Add it to the nav by opening `_data/nav-top.yml` and adding:

```yaml
- title: "Writing"
  url: /writing
```

**Front matter fields for the homepage card:**
- `homepage: true` — makes this page appear in the homepage card stack
- `position` — order on the homepage (lower numbers appear first)
- `summary` — text shown on the card
- `thumbnail` — image shown on the card


## Working with Images

Upload images to `assets/images/`, then reference them in your pages:

```markdown
![Description]({{ site.baseurl }}/assets/images/your-image.jpg)
```

For positioned images with captions, use Xanthan's `figure` component:

```liquid
{% include images/figure.html
  class="right"
  width="40%"
  caption="Your caption here"
  image-path="/assets/images/your-image.jpg"
%}
```

**Naming convention:** lowercase, hyphens between words (e.g., `field-site-2024.jpg`).


## Colors, Fonts, and Style

Xanthan controls all visual design through named CSS variables. You can change the look of your site by editing a handful of lines in `assets/css/base.css` — or just ask an AI to do it:

> "Change my accent color to a deep teal and use a serif font for headings."

See the [Xanthan Styling Guide](docs/editing/colors-and-fonts) for details.


## Using AI to Customize Your Site

Xanthan is designed to work well with AI assistants. Its named variables, documented components, and clear file structure mean you can describe what you want in plain language and get precise, working results.

**A good first prompt:** paste your `_config.yml` and `index.md` into Claude or ChatGPT and write:

> "I'm customizing a portfolio site built on the Xanthan Jekyll framework. Here are my config and homepage. I'm a historian who studies labor movements in the American West. Help me update the title, bio, and summary to reflect my work."

From there you can ask it to change colors, reformat your CV from a Word document, explain any line of code, or generate new page content. You don't need to know CSS or Liquid templates.


## Getting Help

- **Local docs:** the `docs/` folder in your repository has full Xanthan documentation matched to your version
- **Troubleshooting:** [Common issues and fixes](https://xanthan-web.github.io/xanthan/docs/reference/troubleshooting/)
- **ScrollStories:** if you want scroll-driven narrative pages with background images, see `scrollstories/` and the [ScrollStory docs](https://xanthan-web.github.io/xanthan/docs/scrollstories/)
- **Report issues:** [GitHub Issues](https://github.com/xanthan-web/portfolio-template/issues)


