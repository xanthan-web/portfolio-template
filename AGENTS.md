# Working on This Site

> **If you own this site:** you only need to fill in the first section,
> "About this site". Everything after it is written for the AI, and you can
> skip it.

This file guides AI assistants (Claude Code, Codex, Copilot, Cursor and the
like) that edit this site's files directly. It has two parts:

1. **About this site**: the owner's own rules and preferences. The owner writes
   it and you follow it.
2. **How the portfolio template works**: how Xanthan expects this site to be
   built, where things live, and what not to touch. Read all of it before you
   change anything.

**Where the two parts disagree, the owner's rules win.** If following one of
them would break the site (a missing stylesheet, a failed build, an image with
no alt text), say so and ask. Do not quietly break the site, and do not quietly
ignore the rule.

This file is not published on the website (`_config.yml` excludes it), but the
repository is public on GitHub, so anyone can read it there. Keep it free of
anything private.

---

## About this site

> **Owner:** this section is yours. Replace each prompt in italics with your
> own answer, delete the ones you don't care about, and add anything you find
> yourself telling the AI more than once. Short, specific rules work better than
> general ones: "Never use exclamation marks" does more than "keep the tone
> professional". You can also ask the AI to add a rule here for you after a
> session where you corrected it.

### Who I am and what the site is for

_Your name, field and role. Who visits the site: hiring committees, students,
collaborators, editors, the public? What should they come away knowing about
you? For example: "I'm a marine ecologist. Most visitors are prospective
graduate students."_

### Voice

_How the writing on this site should sound. First person or third? Formal or
conversational? US or UK spelling? Words and phrases you never want to see. For
example: "First person, US spelling. Never use 'passionate'."_

### Design

_Colors, fonts, mood. Sites you admire and what you admire about them. Anything
already settled that shouldn't be reopened, such as "the theme is terra-cotta;
don't suggest others"._

### Content rules

_What must stay exactly as you wrote it ("fix typos in my research statement,
never rewrite it"). Which page holds the authoritative version of facts like
dates, titles and affiliations. How you cite publications. Whether images of
people need permission notes._

### How I want to work with you

_How much to explain as you go. Whether to ask before each change or make it
and report back. Whether the AI should commit and push, or leave that to you.
For example: "Make the change, then tell me what you did. I'll push myself."_

---

## How the portfolio template works

### What this site is

A personal or academic website built on [Xanthan](https://xanthan-web.github.io/xanthan/):
pages written in Markdown, built by Jekyll, hosted on GitHub Pages. Bootstrap
handles layout, CSS custom properties control every color and font, and Liquid
includes supply the components. There is no Node, no build step of its own,
and no JavaScript framework.

The owner is the editor and you are the typesetter. Most owners are not web
developers, and many are new to working with an AI on files. Make the change
they asked for, then tell them in plain language what you changed and in which
file. Where it helps, name the one term worth learning ("that block between the
`---` lines is the *front matter*"). Learning the vocabulary is how they get
more precise with their next request.

### Which files belong to the owner and which to Xanthan

| The owner's: edit freely | Xanthan's: leave alone |
|---|---|
| `index.md`, `research.md`, `teaching.md`, `creative.md`, `cv.md`, and any page they add | `_includes/`, `_layouts/` |
| `_config.yml` | `assets/css/` and `assets/js/`, except a theme file the owner made |
| `_data/nav-top.yml`, `_data/nav-profile.yml` | `docs/`, `scrollstories/` |
| `assets/images/`, except the folders in the next column | `assets/images/backgrounds/`, `site/`, `gallery/`, `maps/`; `assets/data/` |
| `assets/css/themes/<their-theme>.css` | `Gemfile`, `.gitignore`, `XANTHAN_CHANGELOG.md`, `scripts/`, `.github/workflows/optimize-images.yml` |

Everything in the right-hand column comes from the Xanthan framework. Taking a
newer version of Xanthan replaces those folders wholesale, so an edit there is
lost on that update and makes the update harder to take. When the owner asks
for something the existing components can't do, tell them so. Change framework
files only when they have asked for that change specifically and understand the
trade-off.

`instructions.md` and `ai.md` are aids for setting up the site. `instructions.md`
walks a new owner through the first edits. `ai.md` is a summary of the framework
for pasting into a chat assistant that cannot see the files. Both can go once
the site is set up. When `instructions.md` is deleted, its entry in
`_data/nav-top.yml` has to go too.

### Where things are

**The homepage** is `index.md`, in three parts from top to bottom:

1. **The profile block**, drawn by `{% include layout/profile-intro.html %}`.
   The photo, name, role, bio and links come from `_data/nav-profile.yml`, not
   from `index.md`. A request to change the name or bio is an edit to that data
   file.
2. **A short introduction** in plain Markdown.
3. **The card stack**: the two Liquid lines at the bottom (`assign essays` and
   `include cards/card-stack.html`). It makes a card for every page whose front
   matter says `homepage: true`. Leave those lines in place.

**Homepage cards** are controlled by front matter on the page being linked to,
not by anything on the homepage:

```yaml
homepage: true                        # show this page as a card
position: 2                           # order; lower numbers come first
summary: One or two sentences for the card.
thumbnail: assets/images/photo.jpg    # the card's image
thumbnail-position: top               # optional: which part of the image to show
thumbnail-zoom: 1.3                   # optional: crop in
```

**The top navigation** is `_data/nav-top.yml`. Each `url` is the file name
without `.md`, with a leading slash: `/research`, not `/research.md`. The nav
adds `baseurl` itself, so don't write it into the URL.

**Site settings** live in `_config.yml`: `title` (shown in the nav bar and the
browser tab), `author`, `description`, `baseurl`, `search`, `analytics_id`, and
`theme_css` once a theme is chosen. A local preview has to be restarted before
it picks up changes to this file.

### Pages

- Every page opens with front matter that has at least a `title` and
  `layout: base`, the homepage included. Use `layout: nav-profile` (a permanent
  profile sidebar) only if the owner asks for one.
- A full-width image header is set in front matter (`header-image`,
  `header-tier`, `header-title`, and so on). See
  `docs/reference/pages-and-front-matter.md`.
- **No raw HTML in pages.** When Markdown can't express a layout, look for a
  component in `docs/reference/component-library.md`. If none fits, tell the
  owner rather than writing a `div`. The owner has to be able to keep editing
  the page as plain Markdown, and a page full of HTML takes that away.
- Components are Liquid includes with hyphenated parameter names:
  `{% include images/figure.html image-path="/assets/images/photo.jpg" caption="..." alt-text="..." %}`.
  **The comment block at the top of each include is the authority on its
  parameters.** Read it before you use the include, rather than copying
  parameters from another page.
- To show Liquid as an example on a page instead of running it, wrap it in
  `{% raw %}` and `{% endraw %}`. Otherwise Jekyll runs it, and usually fails.

### Images

- The owner's images go in `assets/images/`, named in lowercase with hyphens
  (`field-site-2024.jpg`). Their profile photo goes in `assets/images/profile/`.
- Paths start from the site root: `/assets/images/photo.jpg` or
  `assets/images/photo.jpg`. Never `../assets/...`.
- Every image gets alt text that describes it (`alt-text` on the figure
  components, `alt_text` in `nav-profile.yml`). A caption is the fallback.
- Photographs straight from a phone or camera are several megabytes each.
  Resize anything meant for the web to a longest edge of about 1600px. The
  owner can do this without a command line from **Actions → Optimize Images**
  on GitHub (it previews first), or you can run `scripts/optimize-images.sh`
  (see `scripts/README.md`).

### Colors, fonts and style

- Every color, font, spacing and radius is a CSS variable in `:root` of
  `assets/css/base.css`, with semantic names such as `--accent-primary`,
  `--text-body`, `--bg-page` and `--font-heading`.
- **Put the owner's styling in a theme file, not in `base.css`.** Copy
  `assets/css/themes/simple-theme.css` to `assets/css/themes/<name>.css`,
  override the variables there, and set `theme_css: <name>` in `_config.yml`.
  The ready-made themes are `canyon-wall`, `dark-energy` and `terra-cotta`. See
  `docs/reference/themes.md` and `docs/reference/colors-and-fonts.md`.
- Themes override the semantic variables. Don't hardcode hex colors in pages or
  in rules, and don't use the raw palette names (`--sage`, `--golden-clay`)
  outside `:root`.
- Check text contrast against the background it actually sits on: at least
  4.5:1 for body text and 3:1 for large headings.

### The CV

A common request is turning a Word or PDF CV into `cv.md`. Keep the page's
existing structure: `##` for sections, `###` for each entry, an italic line for
the institution and dates, and a horizontal rule between sections. Lines inside
an entry end in two spaces, which is how Markdown makes a line break. **Copy
dates, titles, names and citation details exactly from the source.** Don't
improve, reorder or fill in entries, and list anything ambiguous for the owner
instead of guessing.

### Building and checking

- GitHub Pages builds the site with the `github-pages` gem: Jekyll 3, in safe
  mode, with GitHub's fixed set of plugins. Don't add gems to the `Gemfile` or
  plugins to `_config.yml`, because GitHub will not run them.
- `baseurl` must be the repository name with a leading slash (`/my-site`), or
  empty when the repository is named `USERNAME.github.io`. A wrong `baseurl`
  gives a site with no styling and broken links. Don't add a `url:` line, since
  GitHub supplies it.
- To preview locally, run `bundle exec jekyll serve` and open
  `http://localhost:4000<baseurl>/`, or use `docker compose up`.
  `docs/reference/working-locally.md` covers setup.
- **Before you report a change as done, run `bundle exec jekyll build`** and
  confirm it finishes without errors. Then look at the page you changed in a
  preview if you can. If you couldn't build or preview, say so.
- Pushing does not mean the site is live. GitHub needs a minute or two to
  rebuild, and that build can fail on its own. Check the repository's Actions
  tab, or run `gh run list --limit 3`.

### Git

- Everything in this repository is public. Don't put personal contact details
  on the site that the owner didn't ask to publish.
- Commit when the owner asks you to, with a message that describes the change
  plainly ("Add teaching page and its nav link").
- **Pushing to `main` publishes the site.** Confirm with the owner before you
  push, unless their rules above say otherwise.
- Never force-push or rewrite history on `main`.

### Where to look things up

The `docs/` folder is the documentation for exactly this version of the code.
Trust it over what you remember about Xanthan or about Jekyll in general.

- `docs/reference/component-library.md`: every include, with copyable examples
  and parameter tables
- `docs/reference/pages-and-front-matter.md`: every front matter field
- `docs/reference/colors-and-fonts.md`, `themes.md`, `typography.md`: styling
- `docs/reference/images.md`, `navigation.md`, `search.md`, `tags.md`
- `docs/reference/troubleshooting.md`: common build and display problems
- `docs/scrollstories/`: scroll-driven essays. This is an advanced feature, so
  start from an example in `scrollstories/` rather than writing one from scratch.

The same documentation is online at <https://xanthan-web.github.io/xanthan/docs/>.
