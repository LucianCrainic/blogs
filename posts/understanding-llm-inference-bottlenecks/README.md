---
title: "Example: Understanding LLM Inference Bottlenecks"
description: "Example article demonstrating the blog folder, frontmatter, media, and GitHub-flavored Markdown format."
published: 2026-07-29
updated: 2026-07-29
category: passion
tags:
  - llm
  - inference
  - hpc
draft: true
featured: true
cover: "./cover.svg"
cover_alt: "Abstract diagram of processor tiles connected by flowing memory channels"
---

# Understanding LLM Inference Bottlenecks

> [!NOTE]
> **This is example content.** Replace this folder with a real article when
> ready; it exists to document and exercise the blog format.

Each article lives in its own folder under `posts/`. The folder contains a `README.md` and may
contain a local cover or other article media:

```text
posts/
└── understanding-llm-inference-bottlenecks/
    ├── README.md
    └── cover.svg
```

The folder name creates the stable route: `/blog/understanding-llm-inference-bottlenecks`. An
explicit lowercase `slug` can be added to frontmatter when a route must remain independent of the
folder name.

## Frontmatter is the article contract

Every `README.md` begins with validated YAML metadata. Dates use `YYYY-MM-DD`, category is one of
`work`, `personal`, or `passion`, and tags use lowercase slugs.

| Field         | Required   | Purpose                               |
| ------------- | ---------- | ------------------------------------- |
| `title`       | Yes        | Article and metadata title            |
| `description` | Yes        | Search, cards, and page metadata      |
| `published`   | Yes        | Publication order and RSS date        |
| `updated`     | No         | Shown when different from publication |
| `category`    | Yes        | Primary blog section                  |
| `tags`        | Yes        | Related posts and filters             |
| `draft`       | No         | Excluded from production when `true`  |
| `featured`    | No         | Eligible for featured placement       |
| `cover`       | No         | Path relative to the article README   |
| `cover_alt`   | With cover | Describes a meaningful cover          |

The validator rejects impossible dates, duplicate tags or slugs, unknown categories, missing local
media, and covers without descriptive alternative text.

## Markdown features

Articles support GitHub-flavored Markdown and MDX where it adds real value:

- [x] Tables, task lists, nested lists, and blockquotes
- [x] Footnotes and links
- [x] Heading anchors
- [x] Inline `code` and highlighted code fences
- [x] Responsive images and tables

```cpp
// Fenced code is highlighted by the site build.
double bandwidth_gb_s(double bytes, double seconds) {
  return bytes / seconds / 1'000'000'000.0;
}
```

Images in the article body use normal Markdown and must include useful alt text:

```markdown
![Chart comparing measured memory bandwidth across configurations](./bandwidth.webp)
```

Empty alt text is reserved for truly decorative images. The content validator warns about empty
Markdown alt text so that intent is reviewed.

## Publishing workflow

1. Create a named folder with `README.md`.
2. Add and validate frontmatter.
3. Write the article and keep media beside it.
4. Open a pull request and pass the compatibility workflow.
5. Preview through the portfolio and set `draft: false` when it is ready.
6. Update the portfolio submodule pointer and create a portfolio release tag.

Reading time, category and tag data, related posts, previous/next navigation, RSS metadata, and the
article URL are derived at build time.[^static]

[^static]: The final website is statically generated for GitHub Pages.
