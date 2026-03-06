---
title: Your Name
layout: nav-profile
date: 2024-12-02
---


# Your Name

This is your homepage — the first thing visitors see. Write two or three sentences that introduce who you are and what you do. Think of it as a brief professional statement: your field, your focus, and what makes your work distinctive. Keep it short; the cards below link to your other pages where you can go into depth.

---

The cards below are generated automatically from your other pages. Each page that has `homepage: true` in its front matter will appear here as a card. The card's title, summary text, and thumbnail image all come from that page's front matter:

```yaml
homepage: TRUE
summary: A sentence or two describing this page — appears on the card.
thumbnail: assets/images/your-image.jpg
position: 1   # controls the order cards appear (lower numbers first)
```

To add a new card, create a new page and add those fields. To remove a card, delete `homepage: TRUE` from that page's front matter. To reorder cards, adjust the `position` values.

{% assign essays = site.pages | where: "homepage", true %}
{% include nav/card-stack.html cards = essays %}