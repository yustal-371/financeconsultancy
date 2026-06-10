# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-file static landing page for an investment strategy consultancy. The entire site — HTML, CSS, and JavaScript — lives in one file: `index.html`. There is no build step, no package manager, and no dependencies.

## Running the Site

Open directly in a browser:

```bash
open index.html
```

No server required. All assets are self-contained or loaded from Unsplash CDN URLs.

## Architecture

**Single file: `index.html`**

The file is organized in three embedded blocks in this order:

1. **`<style>`** — All CSS using custom properties defined in `:root`. Layout uses CSS Grid and Flexbox. Responsive breakpoints at `1024px`, `768px`, and `620px`. Scroll animations use the `.fade-in-up` / `.visible` class pattern driven by `IntersectionObserver`.

2. **`<body>` sections** (top to bottom):
   - `#hero` — full-viewport hero with Unsplash background image
   - `#why-us` — 6 benefit cards
   - `#process` — 4-step timeline
   - `#testimonials` — 3 testimonial cards
   - `#lead-magnet` — checklist CTA that scrolls to `#contact`
   - `#contact` — enquiry form (FormSubmit integration)
   - `#faq` — accordion
   - Final CTA banner
   - Footer

3. **`<script>`** — Vanilla JS at bottom of body handling: sticky nav, mobile hamburger, smooth scroll, IntersectionObserver animations, FAQ accordion, and form validation + fetch submission.

## Form Integration

The enquiry form posts to [FormSubmit](https://formsubmit.co/) with the recipient email hardcoded in the `action` attribute:

```html
<form action="https://formsubmit.co/yustal.k@gmail.com" method="POST">
```

Hidden fields control FormSubmit behavior: `_subject`, `_captcha` (disabled), `_template` (table). Form submission uses `fetch()` with `Accept: application/json` to get a JSON response instead of a redirect, showing inline success/error messages without page reload.

## CSS Conventions

- All colors via CSS variables (`--primary`, `--secondary`, `--accent`, `--background`, `--text`, `--light-bg`)
- Section backgrounds alternate between `var(--background)` (white) and `var(--light-bg)` (near-white) with dark sections for Process and Lead Magnet
- Button variants: `.btn-primary` (green), `.btn-secondary` (outline), `.btn-accent` (amber), `.btn-white` (white on green)
- Icons are inline SVG with `stroke` coloring; no icon library is used
