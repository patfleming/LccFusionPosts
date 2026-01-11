---
title: "Customizing Just the Docs"
excerpt: "A practical Just the Docs layout fix that stops wasting screen space and improves sidebar and content readability."

date: 2026-01-11
---

## Introduction

Just the Docs is a strong documentation theme, but its default layout can feel overly constrained—especially for content with diagrams, wide tables, long navigation labels, or dense technical pages. On my site, the sidebar was inset, the main content column was narrower than it needed to be, and long nav entries wrapped in awkward ways.

Rather than chasing small, fragile tweaks, I took a pragmatic approach: identify the real layout choke points (outer wrappers, sidebar sizing, and main-column width caps) and override them directly.

This post shares the working override I’m using.

------

## What this layout override improves

This override is intended to make a docs site feel more “documentation-first” on typical laptops and desktop displays:

- Moves the left navigation area fully to the left edge
- Widens the sidebar to reduce nav wrapping
- Removes width caps so the main content uses available space
- Improves nav label wrapping behavior
- Helps reduce excessive wrapping in the main content area
- (Optional styling) Forces high-contrast table separators for readability

------

## Where to put it

Place this in your Just the Docs customization file:

- `_sass/custom/custom.scss`

(That is the standard customization entry point for Just the Docs.)

------

## The working `custom.scss` override

```
@media (min-width: 50rem) {

  /* Pick your desired sidebar width */
  :root { --navw: 22rem; } /* try 16rem–24rem */

  /* Un-center the outer wrapper (covers JTD version differences) */
  body > .site-wrap,
  body > .site,
  .site-wrap {
    max-width: none !important;
    width: 100% !important;
    margin: 0 !important;
    padding: 0 !important;
  }

  /* Sidebar width */
  .side-bar {
    width: var(--navw) !important;
    min-width: var(--navw) !important;
    max-width: var(--navw) !important;
    flex: 0 0 var(--navw) !important;
  }

  /* Main column starts after sidebar (your working model) */
  .main {
    min-width: 0 !important;
    margin-left: var(--navw) !important;
    padding-left: 0 !important;
    flex: 1 1 auto !important;
  }

  /* Remove width caps so main content can use available width */
  .main,
  .main-content-wrap,
  .main-content,
  .page-content,
  .content,
  .content-wrap {
    max-width: none !important;
    width: auto !important;
  }

  /* Leading/trailing gutters */
  .main-content-wrap {
    margin-left: 0 !important;
    margin-right: 0 !important;
    padding-left: 0 !important;
    padding-right: 0 !important;
  }

  .main-content,
  .main-header {
    padding-left: 1rem !important;
    padding-right: 1rem !important;
  }

  /* Nav wrapping + full width inside sidebar */
  .nav-list .nav-list-link {
    white-space: normal !important;
    overflow-wrap: anywhere;
    word-break: break-word;
    height: auto !important;
    text-overflow: clip !important;
    overflow: visible !important;
    line-height: 1.2;
    max-width: none !important;
  }

  .nav-list-item,
  .nav-list-link {
    max-width: none !important;
  }

  .site-nav,
  .nav-list {
    padding-left: 0 !important;
    padding-right: 0 !important;
    width: 100% !important;
    max-width: none !important;
  }
}
```

------

## What you should change (and what you should not)

The only “knob” I recommend adjusting first is the sidebar width:

```
:root { --navw: 22rem; }
```

Try values in the 16rem–24rem range until the sidebar fits your navigation labels without awkward wrapping.

Everything else in the snippet exists because small, incremental changes tended to break across theme variants and responsive breakpoints. This override is intentionally direct: it removes the width constraints and lets the layout breathe.