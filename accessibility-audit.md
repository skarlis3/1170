# ENGL 1170 — WCAG AA Accessibility Audit

**Date:** April 2026
**Standard:** WCAG 2.1 AA

## Summary

This site is in strong accessibility shape. The nav.js framework dynamically injects skip links, main landmarks, and ARIA labels on all pages. All color combinations pass AA contrast ratios in both light and dark modes. Inline links are underlined for distinguishability. Reduced motion preferences are respected.

Only issue found: two error pages (404.html, not_found.html) were missing `lang="en"` on the `<html>` element.

## Audit Results

| Category | Status | Notes |
|----------|--------|-------|
| Color contrast (light mode) | PASS | All combinations exceed 4.5:1 |
| Color contrast (dark mode) | PASS | All combinations exceed 4.5:1 |
| Language attribute (`lang`) | FIXED | 404.html and not_found.html were missing `lang="en"` |
| Skip links | PASS | Injected dynamically by nav.js on all pages |
| Main landmark | PASS | Injected dynamically by nav.js; index.html has explicit `<main>` |
| Heading hierarchy | PASS | Correct h1 → h2 → h3 order on all pages checked |
| Image alt text | PASS | All images have descriptive alt attributes |
| Link distinguishability | PASS | Inline links in `p` and `li` elements have underlines |
| Focus indicators | PASS | `:focus-visible` styles with 2px solid outline on all interactive elements |
| Keyboard navigation | PASS | All interactive elements reachable via keyboard |
| Reduced motion | PASS | `@media (prefers-reduced-motion: reduce)` present in style.css |
| ARIA labels | PASS | Navigation regions, buttons, and toggles have appropriate aria-labels |
| Empty links | PASS | None found |
| Form labels | PASS | No unlabeled form elements |
| Iframe titles | PASS | Calendar iframes have titles |
| Tabindex | PASS | No positive tabindex values |

## Changes Made

- Added `lang="en"` to `<html>` element in `404.html`
- Added `lang="en"` to `<html>` element in `not_found.html`
