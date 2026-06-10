# LuminaryCapital — Investment Consultancy Landing Page

A single-file static landing page for a professional investment strategy consultancy. The entire site — HTML, CSS, and JavaScript — lives in `index.html` with no build step, no package manager, and no dependencies.

![Site screenshot](screenshot.png)

## Live Site

[https://yustal-371.github.io/financeconsultancy/](https://yustal-371.github.io/financeconsultancy/)

## Running Locally

```bash
open index.html
```

No server required. All assets are self-contained or loaded from Unsplash CDN.

## Structure

Everything is in `index.html`, organised as:

- **`<style>`** — CSS custom properties; deep navy + gold design system; Playfair Display / Inter / DM Mono fonts via Google Fonts; Grid/Flexbox layout; responsive at 1024px, 768px, 620px
- **`<body>`** — Hero → Stats Bar → Why Us (6 cards) → Process (4-step timeline) → Testimonials → Lead Magnet CTA → Contact form → FAQ accordion → Final CTA → Footer
- **`<script>`** — Vanilla JS: sticky nav, mobile hamburger, smooth scroll, IntersectionObserver animations, FAQ accordion, form validation + fetch submission

## Contact Form

Enquiry form posts to [FormSubmit](https://formsubmit.co/) via `fetch()` for a no-redirect JSON response. Inline success/error messages shown without page reload.

## WhatsApp Widget

A floating WhatsApp button sits in the bottom-right corner. Clicking it opens a panel with five pre-written investment query chips. Each chip opens WhatsApp with a pre-filled message to the configured number.

## Deployment

Push to `main` → GitHub Actions workflow (`.github/workflows/deploy.yml`) → GitHub Pages.
