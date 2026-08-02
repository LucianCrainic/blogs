# Lucian Crainic — Blogs

Source content for the blog published through
[luciancrainic.github.io](https://luciancrainic.github.io/blog).

The portfolio repository owns rendering, routes, styling, RSS, and deployment. This repository
owns article Markdown, frontmatter, and article-specific media.

## Content structure

Each article lives in a folder whose name becomes its default URL slug:

```text
posts/
└── example-article/
    ├── README.md
    ├── cover.webp
    └── supporting-diagram.svg
```

Use `README.md` for normal Markdown or `README.mdx` when an article genuinely needs MDX. Keep covers
and supporting images beside the article and reference them with relative paths. Portfolio-local
skills initialize posts and add the supported code, SVG, animation, and Mermaid patterns.

## Frontmatter

Every article starts with validated YAML frontmatter:

```yaml
---
title: "Example article"
description: "A concise description used by cards, metadata, and RSS."
published: 2026-08-02
updated: 2026-08-02
category: passion
tags:
  - example
draft: true
featured: false
cover: "./cover.webp"
cover_alt: "Descriptive alternative text for the cover"
---
```

Categories currently supported by the portfolio are `work`, `personal`, and `passion`. Tags and
explicit `slug` values use lowercase kebab case. Keep `draft: true` until an article is ready for a
portfolio release.

Pull requests and pushes to `main` validate the content against the portfolio's current schema.
Merging a post does not publish it automatically: the portfolio must update its pinned submodule
commit and create its normal release tag.

## Rich article content

- Use ordinary fenced code with an exact language; the portfolio applies syntax highlighting,
  responsive overflow, and copy behavior.
- Embed static or animated SVG files with Markdown. Give every meaningful image useful alternative
  text, include a `viewBox`, support light and dark palettes, and disable animation for
  `prefers-reduced-motion`.
- Author Mermaid diagrams as fenced `mermaid` blocks with `accTitle` and `accDescr`. The portfolio
  renders light and dark SVG variants at build time; articles must not load Mermaid from a CDN.
- Preview and validate every new content type through the portfolio before publishing.
