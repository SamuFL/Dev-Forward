# Copilot Instructions

## Project Overview

Dev:Forward ("Next Commit") is a static single-page website for a community event targeting Vienna's developer community. The site is a landing page for an AI-Assisted Development meetup planned for May/June 2026.

## Architecture

- **Single-file site:** Everything lives in `index.html` — markup, styles, and scripts are all inline. There is no build step, no bundler, no framework.
- **No dependencies:** No `package.json`, no npm modules. Fonts are loaded from Google Fonts CDN.
- **Content language:** The site is bilingual — **English by default**, with a German toggle. All copy must be maintained in both languages inside the `i18n` object in `index.html` (`en` and `de` keys).

## Style & Design Conventions

- CSS custom properties defined in `:root` control the entire color scheme (dark theme with cyan accent `#22d3ee`).
- Two font families: **Outfit** (display/body) and **JetBrains Mono** (code/labels).
- Section labels use a `// comment` style (`// why`, `// status`) rendered in monospace — keep this pattern for new sections (add translations for both `en` and `de` keys).
- Cards in `.card-grid` are wrapped in `<a>` tags with `mailto:` links — interaction cards should follow this pattern.
- Scroll-reveal animations are applied via the `.reveal` CSS class and a small `IntersectionObserver` script at the bottom.
- The `EN | DE` language toggle (`.lang-toggle`, fixed top-right) uses `data-i18n` attributes on elements and an `applyLang(lang)` function. When adding new translatable text, add a `data-i18n="your-key"` attribute to the element and add both `en` and `de` entries to the `i18n` object in the `<script>` block. Language preference is persisted in `localStorage`.

## Project Plan

The living project plan lives in the **private** repo [`SamuFL/Dev-Forward-internal-planning`](https://github.com/SamuFL/Dev-Forward-internal-planning) (`PLAN.md`). It is written in German and contains phase-by-phase tasks, the contact/status tracker, and open decisions.

**Keep `PLAN.md` and `index.html` in sync:** when event details change (date, venue, programme, speaker lineup, status items), update both files. The status section, format grid, and "get involved" cards in `index.html` are the most likely to need updating.

## Deployment

The site is deployed via **GitHub Pages** directly from the `main` branch. Push to `main` = live.
