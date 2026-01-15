---
title: Alexandra Ruiz
layout: nav-profile
date: 2024-12-02
---


# Alexandra Ruiz

I am a History PhD Candidate focusing on creating more engaging history through emerging technology. This site is built with [Xanthan](https://xanthan-web.github.io) using GitHub Pages, a free platform for web hosting that gives me full control over my content, files, and style.

{% assign essays = site.pages | where: "homepage", true %}
{% include nav/card-stack.html cards = essays %}