---
title: Getting Started with Your Portfolio
layout: base
---

# Customizing Your Portfolio Template

**Welcome!** This page walks you through personalizing this portfolio template to showcase your work, research, and creative projects. Once you're comfortable editing and have updated the main sections, **you can delete this file**—it's just here to help you get started.

## What You Have

This portfolio template includes:
- **Homepage** (`index.md`) with your name and card links to main sections
- **Research page** (`research.md`) for academic work and publications
- **Teaching page** (`teaching.md`) for courses and pedagogy
- **Creative page** (`creative.md`) for projects, exhibitions, and creative work
- **CV page** (`cv.md`) for your full curriculum vitae
- **ScrollStories folder** (`scrollstories/`) for visual narrative essays
- **Map page** (`map.md`) for geospatial projects
- All styling, navigation, and design pre-configured


## Quick Start: Open the Editor

The easiest way to edit your site is using GitHub's built-in VS Code editor:

1. Go to your repository on GitHub
2. Press the **`.` (period) key** on your keyboard
   - VS Code opens in your browser
   - All your files appear in the left sidebar
3. Start editing!

**To save changes:** Press **Ctrl+S** (Windows/Linux) or **Cmd+S** (Mac)


## First Steps: Personalize Your Site

### 1. Update Your Name and Bio (`index.md`)

Open `index.md` and change:
- **Your name** in the title and heading
- **Your bio paragraph** — describe your work and interests
- Keep the card stack code at the bottom (it auto-generates links to your pages)

```yaml
---
title: Your Name Here
layout: nav-profile
---

# Your Name Here

Write a short intro about yourself and your work...
```


### 2. Edit the Research Page (`research.md`)

Open `research.md` and replace the sample content:
- Add your publications, papers, and projects
- Update descriptions and links
- Change the summary in the front matter (top section)


### 3. Update Teaching (`teaching.md`)

Open `teaching.md` and add:
- Courses you've taught
- Your teaching philosophy
- Student projects or examples


### 4. Customize Creative Work (`creative.md`)

Open `creative.md` and showcase:
- Exhibitions, installations, or performances
- Digital projects or multimedia work
- Creative collaborations


### 5. Replace the CV (`cv.md`)

Open `cv.md` and update with your actual CV:
- Education, experience, awards
- Publications and presentations
- Skills and competencies


## Adding a New Page

Want to add a page (like "Blog" or "Projects")? Here's how:

### Step 1: Create the Page File

1. Right-click in the root folder (where `index.md` lives)
2. Select **"New File"**
3. Name it something like `blog.md` or `projects.md`
4. Add front matter at the top:

```yaml
---
title: Blog
layout: base
homepage: true
position: 5
summary: Thoughts and updates from my research journey.
thumbnail: assets/images/your-image.jpg
---

# Blog

Your content here...
```

**Front matter explained:**
- `homepage: true` — makes it appear on your homepage card stack
- `position: 5` — controls the order (lower numbers = earlier in the list)
- `summary` — text shown on the homepage card
- `thumbnail` — image shown on the homepage card


### Step 2: Add to Navigation Bar

To make your new page appear in the top navigation:

1. Open `_data/top-nav.yml`
2. Add a new entry:

```yaml
- title: "Blog"
  url: /blog
```

Save and your new page appears in the nav bar!


## Working with Images

### Adding Images to Your Pages

1. Upload images to `assets/images/` folder:
   - Right-click on `assets/images/`
   - Select **"Upload..."**
   - Choose your image files

2. Reference images in your markdown files:
   ```markdown
   ![Description of image]({{ site.baseurl }}/assets/images/your-image.jpg)
   ```

**Image naming tips:**
- Use lowercase only
- Use hyphens between words (e.g., `field-site-2024.jpg`)
- Make names descriptive


### Using Xanthan's Image Components

For more control over image display, use Xanthan's built-in includes:

```liquid
{% include images/figure.html
  class="right"
  width="40%"
  caption="Your caption here"
  image-path="/assets/images/your-image.jpg"
%}
```

See the [Xanthan Image Documentation](https://xanthan-web.github.io/xanthan/docs/content-design/images/) for all options.


## Customizing Your Site

### Update Site Settings (`_config.yml`)

Open `_config.yml` to change:
- **Site title and description**
- **Your URL** (if you have a custom domain)
- **Author info**

```yaml
title: Your Name - Portfolio
description: Academic portfolio and digital research
url: "https://yourusername.github.io"
baseurl: ""
```


### Modify Navigation

Navigation is controlled by YAML files in `_data/`:

- **`top-nav.yml`** — Top navigation bar
- **`sidebar.yml`** — Left sidebar navigation (if using that layout)
- **`nav-profile.yml`** — Profile sidebar settings

Just edit these files to add/remove/reorder menu items.


### Change Colors and Styles

For custom colors, fonts, and styling:
1. Read the [Xanthan Styling Guide](https://xanthan-web.github.io/xanthan/docs/content-design/styling/)
2. Add custom CSS in `_includes/` or `assets/css/`
3. Override Xanthan defaults in your own style files


## Using Markdown

You don't need to know HTML! Use simple markdown:

```markdown
# Big Heading

## Smaller Heading

**Bold text**

*Italic text*

[Link text](https://example.com)

- Bullet point
- Another point

1. Numbered list
2. Second item
```

**See examples** in the existing pages—just copy the formatting you like!


### ScrollStories

For visual narrative essays with scrolling effects:
- Check the `scrollstories/` folder for examples
- Read the [ScrollStory Documentation](https://xanthan-web.github.io/xanthan/docs/scrollstories/)
- Create immersive stories with background images and scrolling text


## Getting Help

### Xanthan Documentation

Your template is built on **Xanthan**, which has extensive docs:
- **Browse local docs**: `/docs/` folder in your repository
- **Online docs**: [xanthan-web.github.io/xanthan/docs/](https://xanthan-web.github.io/xanthan/docs/)
- **Troubleshooting**: [Common issues and fixes](https://xanthan-web.github.io/xanthan/docs/content-design/troubleshooting/)


### Use AI Assistance

AI tools like Claude or ChatGPT can help:
- "How do I add a two-column layout in markdown?"
- "Can you help me create a publications list?"
- "How do I change the navigation order?"
- "What's wrong with this YAML?" (paste your code)

Check out the [Using AI with Xanthan Guide](https://xanthan-web.github.io/xanthan/docs/content-design/using-ai-assistance/) for tips.


### Community and Support

- **Report issues**: [GitHub Issues](https://github.com/xanthan-web/portfolio-template/issues)
- **Xanthan community**: Check the main Xanthan repo for discussions


## Clean Up When Ready

Once you've customized your portfolio and feel comfortable editing:

1. **Delete this file** (`instructions.md`)
   - Right-click in VS Code and select "Delete"
2. **Remove from navigation** (if you added it to `nav-top.yml`)
3. Keep updating your portfolio with new work!


## Quick Reference

### Essential Files
- `index.md` — Homepage
- `research.md`, `teaching.md`, `creative.md`, `cv.md` — Main pages
- `_config.yml` — Site settings
- `_data/nav-top.yml` — Navigation menu
- `assets/images/` — Image storage

### Common Tasks
- **Add page**: Create `.md` file, add to `top-nav.yml`
- **Add image**: Upload to `assets/images/`, reference with `![](path)`
- **Edit nav**: Open `_data/top-nav.yml` or `sidebar.yml`
- **Change layout**: Update `layout:` in page front matter

### Helpful Links
- [Xanthan Docs](https://xanthan-web.github.io/xanthan/docs/)
- [Markdown Guide](https://www.markdownguide.org/)
- [GitHub Pages Help](https://docs.github.com/en/pages)

---

{: .text-center .text-muted}
**Questions?** Check the [Xanthan documentation](https://xanthan-web.github.io/xanthan/) or [open an issue](https://github.com/xanthan-web/portfolio-template/issues).
