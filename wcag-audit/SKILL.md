---
name: wcag-audit
description: Audit web accessibility against WCAG 2.1/2.2 AA. Scans UI code for violations across 11 categories (images, forms, keyboard, ARIA, structure, tables, frames, color contrast, etc.) with axe-core impact levels. Use when checking accessibility, preparing for compliance, or reviewing UI components.
license: MIT
compatibility: Works with any web project (HTML, React, Vue, Angular, Svelte). Read-only audit — no modifications.
metadata:
  author: christopherlouet
  version: "1.0"
  source: https://github.com/christopherlouet/wcag-audit
---

# WCAG Accessibility Audit

Perform a comprehensive accessibility audit of UI code based on WCAG 2.1/2.2 level AA, inspired by the axe-core rule set (93+ rules).

## Workflow

1. Scan UI files (components, pages, layouts, CSS/SCSS)
2. Audit all 11 categories systematically
3. Classify each issue by impact level (Critical/Serious/Moderate/Minor)
4. Distinguish violations (auto-detectable) from needs-review (manual check required)
5. Report with file:line references and concrete fix suggestions

## Impact Levels (axe-core aligned)

| Level | Definition | Action |
|-------|-----------|--------|
| **Critical** | Completely blocks access for some users | Fix immediately |
| **Serious** | Significant impact on usability | Fix before release |
| **Moderate** | Degrades user experience | Plan fix |
| **Minor** | Desirable improvement | Backlog |

## Audit Categories

| # | Category | Key Rules | WCAG |
|---|----------|----------|------|
| 1 | Images & media | alt text, SVG, object, video captions, autoplay | 1.1.1, 1.2.2, 1.4.2 |
| 2 | Forms | labels, select, error messages, autocomplete | 4.1.2, 3.3.1, 1.3.5 |
| 3 | Keyboard | focus visible, traps, skip-link, scrollable regions, nested interactive | 2.1.1, 2.1.2, 2.4.1 |
| 4 | Buttons & links | accessible names, descriptive links, link-in-text-block | 4.1.2, 2.4.4 |
| 5 | Color & contrast | AA ratios (4.5:1 / 3:1), color-only indicators, UI elements | 1.4.3, 1.4.1, 1.4.11 |
| 6 | ARIA | allowed/required/prohibited attrs, valid roles, parent/child, aria-hidden+focus | 4.1.2, 1.3.1 |
| 7 | Structure & semantics | html lang, title, heading hierarchy, landmarks, regions, lists | 3.1.1, 2.4.2, 1.3.1 |
| 8 | Tables | th, scope, headers, caption | 1.3.1 |
| 9 | Frames & iframes | title, uniqueness, focus | 4.1.2, 2.1.1 |
| 10 | Deprecated elements | blink, marquee, meta-refresh, autoplay | 2.2.1, 2.2.2 |
| 11 | WCAG 2.2 | target size 44x44px, focus not obscured | 2.5.8, 2.4.11 |

For detailed rules per category, see [references/RULES.md](references/RULES.md).

## Detection Patterns

Use these regex patterns to find common violations:

### Images
```
<img(?![^>]*alt=)
<svg(?![^>]*aria-label)(?![^>]*role="presentation")
<input\s[^>]*type="image"(?![^>]*alt=)
<object(?![^>]*aria-label)(?![^>]*title=)
```

### Forms
```
<input(?![^>]*aria-label)(?![^>]*id=.*<label[^>]*for=)
<select(?![^>]*aria-label)(?![^>]*id=)
```

### ARIA
```
role="(?!alert|button|checkbox|dialog|grid|img|link|list|listbox|menu|menubar|menuitem|navigation|option|progressbar|radio|region|search|slider|tab|tablist|tabpanel|textbox|timer|toolbar|tooltip|tree|treeitem)[a-z]+"
aria-hidden=["']true["'][^>]*tabindex=(?!["']-1)
```

### Structure
```
<html(?![^>]*lang=)
<title>\s*</title>
```

### Tables & frames
```
<table(?![^>]*role=["']presentation)(?![\s\S]*?<th)
<th(?![^>]*scope=)
<iframe(?![^>]*title=)
```

### Deprecated elements
```
<blink
<marquee
<meta[^>]*http-equiv=["']refresh
autoplay(?![^>]*muted)
```

## Expected Output

### Accessibility Score
```
Target level: AA (WCAG 2.1/2.2)
Score: [X/100]
Violations: [N] (Critical: X, Serious: X, Moderate: X, Minor: X)
Needs Review: [N]
```

### Violations (auto-detected)

| Impact | Category | WCAG | Element | File:line | Fix |
|--------|----------|------|---------|-----------|-----|
| Critical | Images | 1.1.1 | `<img>` missing alt | Button.tsx:12 | Add `alt="..."` |
| Serious | ARIA | 4.1.2 | invalid role | Modal.tsx:8 | Use a valid ARIA role |

### Needs Review (manual check required)

| Category | Element | File:line | Check |
|----------|---------|-----------|-------|
| Color | inline color | Card.tsx:15 | Verify contrast ratio >= 4.5:1 |
| Images | alt present | Hero.tsx:3 | Verify alt text is meaningful |

### Prioritized Recommendations
1. [Critical] ...
2. [Serious] ...
3. [Moderate] ...

## Complementary Runtime Tools

For a complete runtime audit, use in addition:
- **axe-core**: `npx @axe-core/cli http://localhost:3000`
- **Playwright + axe**: `@axe-core/playwright` for E2E accessibility tests
- **Pa11y**: `npx pa11y http://localhost:3000`
- **Lighthouse**: Accessibility tab in Chrome DevTools

## Directives

- Audit all 11 categories systematically
- Classify every issue by impact level
- Distinguish violations (auto-detectable) from needs-review (manual)
- Propose concrete fixes with code examples
- Never ignore decorative images (they must have `alt=""`)
- Never skip Critical violations
- Target WCAG 2.1/2.2 level AA minimum

Think carefully about the experience of users with disabilities.
