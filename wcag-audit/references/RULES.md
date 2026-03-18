# WCAG Audit Rules Reference

Complete rule set organized by category, with impact levels and WCAG criteria references. Inspired by axe-core (93+ rules).

## 1. Images & Media

| Rule | Impact | WCAG |
|------|--------|------|
| Every `<img>` must have an `alt` attribute | Critical | 1.1.1 |
| Decorative images: `alt=""` with `role="presentation"` | Serious | 1.1.1 |
| SVG with `role="img"` must have `aria-label` or `<title>` | Serious | 1.1.1 |
| `<input type="image">` must have `alt` | Critical | 1.1.1 |
| `<object>` and `<embed>` must have alternative text | Serious | 1.1.1 |
| `<area>` in image maps must have `alt` | Critical | 1.1.1 |
| Videos must have captions (`<track kind="captions">`) | Critical | 1.2.2 |
| No autoplay audio (or provide stop control) | Serious | 1.4.2 |

## 2. Forms

| Rule | Impact | WCAG |
|------|--------|------|
| Every input must have an associated `<label>` (`htmlFor` or nesting) | Critical | 4.1.2 |
| `<select>` must have an accessible name | Critical | 4.1.2 |
| Errors must use `aria-invalid` and `role="alert"` | Serious | 3.3.1 |
| Hints with `aria-describedby` | Moderate | 3.3.2 |
| Valid and relevant `autocomplete` attributes | Moderate | 1.3.5 |
| No multiple labels on the same field | Moderate | 4.1.2 |

## 3. Keyboard Navigation

| Rule | Impact | WCAG |
|------|--------|------|
| Visible focus required (`:focus-visible` with `outline`) | Serious | 2.4.7 |
| Never use positive `tabIndex` | Serious | 2.4.3 |
| Site must be 100% keyboard navigable | Critical | 2.1.1 |
| No keyboard traps (focus must not get stuck) | Critical | 2.1.2 |
| "Skip to content" link at page start | Serious | 2.4.1 |
| Scrollable regions must be focusable | Serious | 2.1.1 |
| No nested interactive elements (button inside button) | Serious | 4.1.2 |

## 4. Buttons & Links

| Rule | Impact | WCAG |
|------|--------|------|
| Buttons must have accessible text | Critical | 4.1.2 |
| Icon buttons must have `aria-label` | Critical | 4.1.2 |
| Descriptive links (not "click here") | Serious | 2.4.4 |
| External links: indicate new tab opening via `sr-only` | Moderate | 2.4.4 |
| Links in text blocks distinguishable without color alone | Serious | 1.4.1 |

## 5. Color & Contrast

| Rule | Impact | WCAG |
|------|--------|------|
| Normal text: minimum ratio 4.5:1 | Serious | 1.4.3 |
| Large text (18px+ or 14px+ bold): minimum ratio 3:1 | Serious | 1.4.3 |
| UI elements and graphics: minimum ratio 3:1 | Serious | 1.4.11 |
| Never use color as the only indicator | Serious | 1.4.1 |

## 6. ARIA

| Rule | Impact | WCAG |
|------|--------|------|
| Only allowed ARIA attributes for the role used | Critical | 4.1.2 |
| Required ARIA attributes present per role | Critical | 4.1.2 |
| No prohibited ARIA attributes for the role | Serious | 4.1.2 |
| Valid ARIA attribute values | Critical | 4.1.2 |
| Valid ARIA roles (no invented roles) | Critical | 4.1.2 |
| No deprecated ARIA roles | Moderate | 4.1.2 |
| `aria-hidden="true"` must not be on focusable elements | Critical | 4.1.2 |
| `aria-hidden="true"` forbidden on `<body>` | Critical | 4.1.2 |
| ARIA parent/child relationships respected (e.g., listbox > option) | Serious | 1.3.1 |
| ARIA components named: dialog, meter, progressbar, tooltip | Serious | 4.1.2 |

## 7. Structure & Semantics

| Rule | Impact | WCAG |
|------|--------|------|
| `<html>` must have a valid `lang` attribute | Serious | 3.1.1 |
| `<title>` must be non-empty and descriptive | Serious | 2.4.2 |
| Heading hierarchy respected (no h1 > h3 jumps) | Moderate | 1.3.1 |
| Headings must not be empty | Serious | 2.4.6 |
| Page contains an `<h1>` | Moderate | 1.3.1 |
| Landmarks used (`<main>`, `<nav>`, `<header>`, `<footer>`) | Moderate | 1.3.1 |
| Same-type landmarks have unique labels (`aria-label`) | Moderate | 2.4.1 |
| All page content within a landmark (`<main>`) | Moderate | 1.3.1 |
| Lists properly structured (`<ul>/<ol>` > `<li>`) | Moderate | 1.3.1 |
| Foreign language passages marked (`lang` on element) | Minor | 3.1.2 |

## 8. Tables

| Rule | Impact | WCAG |
|------|--------|------|
| Data tables must have `<th>` elements | Serious | 1.3.1 |
| `<th>` must have a `scope` attribute (col/row) | Serious | 1.3.1 |
| `<td headers="">` must reference existing `<th>` elements | Serious | 1.3.1 |
| `<th>` must not be empty | Serious | 1.3.1 |
| `<caption>` and `summary` must not be identical | Minor | 1.3.1 |

## 9. Frames & Iframes

| Rule | Impact | WCAG |
|------|--------|------|
| Every `<iframe>` must have a `title` attribute | Serious | 4.1.2 |
| Iframe titles must be unique on the page | Moderate | 4.1.2 |
| Iframe with focusable content must not have `tabindex="-1"` | Serious | 2.1.1 |

## 10. Deprecated & Dangerous Elements

| Rule | Impact | WCAG |
|------|--------|------|
| Do not use `<blink>` | Serious | 2.2.2 |
| Do not use `<marquee>` | Serious | 2.2.2 |
| No `<meta http-equiv="refresh">` with delay | Serious | 2.2.1 |
| No autoplay audio/video without control | Serious | 1.4.2 |

## 11. WCAG 2.2

| Rule | Impact | WCAG |
|------|--------|------|
| Touch targets minimum 44x44px (buttons, links, inputs) | Serious | 2.5.8 |
| Focus must not be obscured by other elements | Serious | 2.4.11 |
