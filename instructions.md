---
title: Getting Started with Your Portfolio
layout: base
---

# Customizing Your Portfolio Template

This page walks you through personalizing this portfolio template to showcase your work, research, and creative projects. Once you're comfortable editing and have updated the main sections, **you can delete this file**—it's just here to help you get started.

## What You Have

This portfolio template includes:
- **Homepage** (`index.md`) with your name and card links to main sections
- **Research page** (`research.md`) for academic work and publications
- **Teaching page** (`teaching.md`) for courses and pedagogy
- **Creative page** (`creative.md`) for projects, exhibitions, and creative work
- **CV page** (`cv.md`) for your full curriculum vitae
- **Instructions** (`instructions.md`) for updating your new site!
- **Docs** (`docs folder`) with full Xanthan documentation (since Xanthan itself may have changed a bit)



## Quick Start: Open the Editor
The easiest way to edit your site is using GitHub's built-in editor:

1. Go to your repository on GitHub
2. Press the **`.` (period) key** on your keyboard
   - VS Code opens in your browser
   - All your files appear in the left sidebar
3. Start editing!

**To save changes:** Press **Ctrl+S** (Windows/Linux) or **Cmd+S** (Mac)


## Using AI to Customize Your Site

Xanthan is designed to be legible to AI assistants. Its named CSS variables, documented components, and clear file structure mean you can describe what you want in plain language and get precise, working results.

**Try this as your first AI conversation.** Paste your `_config.yml` and `index.md` into Claude or ChatGPT, then write something like:

> "I'm customizing a portfolio site built on the Xanthan Jekyll framework. Here are my main config file and homepage. I'm a historian who studies labor movements in the American West. Can you help me update the title, bio, and summary to reflect my work and interests?"

From there, you can ask it to:
- Change colors or fonts ("make the accent color a deep navy blue")
- Add or reorder navigation items
- Format your CV or publications list from a Word document
- Explain what any line of code does

You don't need to know CSS or Liquid templates. Describe what you want; the AI does the technical work.


## 1. Update Your Name and Bio (`index.md`)

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


## 2. Edit or delete included pages 
- `research.md`
- `teaching.md`
- `creative.md`
- `cv.md` (and see the note on that page about using AI to reformat a Word doc for your webpage.)


## 3. Adding a New Page

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

See the [Xanthan Docs on your site](docs) for all options.


## Update site metadata 

Open `_config.yml` to change:
- **Site title and description**
- **Your URL** (if you have a custom domain)
- **Author info**

Your file should look something like:

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

For custom colors, fonts, and styling, read the [Xanthan Styling Guide](docs/content-design). Again, AI can help you do whatever you need with plain language. 


## Using Markdown

You'll want to use headings, italics, and other basic typography on your site. Use simple markdown:

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
