---
title: Portfolio Template
layout: nav-profile
date: 2024-12-02
---


# Portfolio Template for Xanthan

A ready-to-use template for building a personal academic or professional portfolio site. This template is part of [Xanthan](https://xanthan-web.github.io).

This page is the `index.md` file in your repository. You'll eventually replace everything here with your own name, photo, and introduction.

All the instructions for setting up your portfolio are on the **[Instructions page](instructions)**.


## Documentation
- 📖 [Complete Xanthan Docs](docs/) — Your site has all the docs for your template
- 🎨 [Design & Content](docs/content-design/) — Colors, fonts, images
- 🏗️ [Navigation](docs/navigation/) — How to organize pages


## Questions or Problems?
- Check the [troubleshooting guide](docs/content-design/troubleshooting)
- Ask an AI assistant (Claude, ChatGPT) — They're great at helping customize templates
- [Report an issue](https://github.com/xanthan-web/portfolio-template/issues) on GitHub

---

## Sample Pages

The cards below link to the sample pages included with this template. Browse them to see what's possible, then customize each one with your own content.

{% assign essays = site.pages | where: "homepage", true %}
{% include nav/card-stack.html cards = essays %}