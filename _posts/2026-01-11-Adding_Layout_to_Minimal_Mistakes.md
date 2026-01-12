---
title: "Adding Layout Options to Minimal Mistakes"
excerpt: "Shows how and why an extra-wide layout option was added to Minimal Mistakes to better support wide, reference-style content."

date: 2026-01-11

categories: Tutorials
tags: [jekyll, theming, site-tooling]

---

## Introduction

Most blog themes—including Minimal Mistakes—are optimized for linear reading: centered text, generous margins, and relatively narrow columns. That works well for narrative posts, but it becomes limiting for content that benefits from horizontal context, such as diagrams, tables, screenshots, comparisons, or reference-style navigation.

While refining the LCC Fusion Posts site, I added an **opt-in extra-wide layout option** to complement the existing layouts provided by Minimal Mistakes. This post explains *why* an additional layout option was useful, *what* it changes, and *how* it was added in a way that remains compatible with the theme.

------

## Why add another layout option?

Some posts benefit from seeing more information side by side:

- diagrams and schematics
- tables with multiple columns
- screenshots or UI walkthroughs
- comparisons and matrices
- reference and how-to material with navigation

On a typical laptop screen, these posts were using only about half of the available width, with large white margins on both sides. Disabling optional elements such as the table of contents or author profile did not reclaim that space—the underlying page container remained constrained.

The result was excessive line wrapping, cramped visuals, and inefficient use of available screen real estate.

The goal was not to change the default look of the site, but to introduce a **clear, intentional layout option** for posts where horizontal space improves clarity.

------

## Why the existing `wide` class wasn’t sufficient

Minimal Mistakes already provides a `wide` class, so that was the first option explored.

While `wide` slightly adjusts padding, it does **not** expand the actual page container. In addition, enabling `wide` changes how the table of contents behaves:

- the TOC moves from the right-hand side to the **top of the page**
- vertical space is consumed before any content appears
- the limited horizontal gain does not offset the loss of vertical space

Placing the TOC at the top can be useful in some cases, but for reference-style content it proved to be a poor tradeoff. The page still felt narrow, and usable space was shifted rather than expanded.

This made it clear that a separate layout option was needed—one that addressed the container width directly without rearranging navigation elements.

------

## What the `extra-wide` layout does

The new `extra-wide` layout option focuses on the actual bottleneck: the page container.

When enabled, `extra-wide`:

- allows the page container to expand to the full viewport width
- preserves the default layout for posts that don’t opt in
- keeps the table of contents on the **right-hand side**, using otherwise unused space
- works cleanly with optional elements such as the TOC and author profile

This makes it possible to enable navigation and metadata without sacrificing space for the main content.

------

## How to enable the extra-wide layout

Enable the layout by adding `extra-wide` to a post’s front matter:

```
layout: single
classes:
  - extra-wide
```

The `wide` class is intentionally omitted for posts using `extra-wide`, since it alters TOC placement without meaningfully improving space usage.

------

## What changed in the site CSS

To support this layout option, a small, targeted CSS override was added to the site’s main stylesheet. The override is opt-in and only applies when `extra-wide` is present.

In `assets/css/main.scss`, after the Minimal Mistakes imports, the following block was added:

```
/* =========================================================
   Extra-wide mode (opt-in via front matter: classes: [extra-wide])
   ========================================================= */

@media (min-width: 64em) {

  /* Widen the actual page container */
  body.layout--single.extra-wide .initial-content {
    box-sizing: border-box;
    width: 100vw;
    max-width: 100vw;
    margin: 0;
    padding-left: 12px;
    padding-right: 12px;
  }

  /* Ensure content follows the widened container */
  body.layout--single.extra-wide #main,
  body.layout--single.extra-wide #main > article.page,
  body.layout--single.extra-wide #main > article.page > .page__inner-wrap,
  body.layout--single.extra-wide #main > article.page > .page__inner-wrap > .page__content {
    box-sizing: border-box;
    width: 100%;
    max-width: none;
    margin-left: 0;
    margin-right: 0;
    float: none;
  }
}
```

This leaves all default layouts untouched and activates only when explicitly requested.

------

## Optional elements in extra-wide mode

### Table of Contents

With the extra-wide layout enabled, the table of contents becomes additive rather than competitive.

The TOC remains on the right-hand side of the page and occupies space that would otherwise be unused. It no longer compresses the article or forces awkward line wrapping, making it especially useful for longer reference or how-to posts.

Example:

```
toc: true
classes:
  - extra-wide
```

### Author profile

The author profile can also be enabled without affecting content width. When turned on, it appears in the upper-left area of the page and does not reduce the usable space for the article.

For LCC Fusion posts, the profile is intentionally disabled so the focus remains on the content itself rather than the author. The important point is that this is now a **content decision**, not a layout compromise.

------

## When to use the extra-wide layout

The extra-wide layout is a good fit for posts that include:

- visuals that benefit from side-by-side viewing
- wide tables or comparison grids
- screenshots or step-by-step walkthroughs
- reference material with navigation aids

For narrative or essay-style posts, the default Minimal Mistakes layout remains a better fit.

------

## A small change with a meaningful impact

This addition doesn’t replace existing layouts or redefine theme defaults. It simply adds a missing option: a way for content that benefits from horizontal context to use available screen space efficiently—without rearranging navigation or metadata.

By separating `extra-wide` from `wide`, each layout option now has a clear purpose, and posts can choose the presentation that best supports understanding.