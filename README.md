# wcag-audit

![Version](https://img.shields.io/badge/version-1.1-blue) ![WCAG](https://img.shields.io/badge/WCAG-2.1%2F2.2%20AA-green) ![License](https://img.shields.io/badge/license-MIT-brightgreen)

An [Agent Skill](https://agentskills.io) for auditing web accessibility against WCAG 2.1/2.2 level AA, inspired by [axe-core](https://github.com/dequelabs/axe-core) (93+ rules).

## Install

```bash
npx skills add christopherlouet/wcag-audit
```

## Usage

Ask your AI agent to audit accessibility:

```
> Audit the accessibility of my login page
> Check WCAG compliance on src/components/
> Review this form for accessibility issues
> Are there any a11y violations in the navigation component?
```

The skill activates automatically when you mention accessibility, WCAG, a11y, screen readers, or ask to review UI components for compliance.

## What it does

Scans your UI code (React, Vue, Angular, Svelte, HTML) for accessibility violations across **11 categories**:

| # | Category | WCAG Criteria |
|---|----------|--------------|
| 1 | Images & media | 1.1.1, 1.2.2, 1.4.2 |
| 2 | Forms | 4.1.2, 3.3.1, 1.3.5 |
| 3 | Keyboard navigation | 2.1.1, 2.1.2, 2.4.1 |
| 4 | Buttons & links | 4.1.2, 2.4.4 |
| 5 | Color & contrast | 1.4.3, 1.4.1, 1.4.11 |
| 6 | ARIA | 4.1.2, 1.3.1 |
| 7 | Structure & semantics | 3.1.1, 2.4.2, 1.3.1 |
| 8 | Tables | 1.3.1 |
| 9 | Frames & iframes | 4.1.2, 2.1.1 |
| 10 | Deprecated elements | 2.2.1, 2.2.2 |
| 11 | WCAG 2.2 | 2.5.8, 2.4.11 |

Each issue is classified by **impact level** (Critical / Serious / Moderate / Minor) aligned with axe-core, and distinguished as **violation** (auto-detected) or **needs review** (manual check).

## Output

The audit produces:
- Accessibility score out of 100
- Violations table with impact, WCAG ref, file:line, and fix suggestion
- Needs-review items requiring manual verification
- Prioritized recommendations

## Skill contents

```
wcag-audit/
├── SKILL.md                   # Main skill instructions
└── references/
    ├── RULES.md               # 60+ rules across 11 categories
    ├── PATTERNS.md            # Regex patterns for violation detection
    ├── EXAMPLES.md            # Good/bad code examples per category
    └── CHECKLIST.md           # Manual review checklist (needs-review items)
```

## Complementary tools

For runtime audits, use alongside:
- [axe-core](https://github.com/dequelabs/axe-core): `npx @axe-core/cli URL`
- [Playwright + axe](https://www.npmjs.com/package/@axe-core/playwright): E2E accessibility tests
- [Pa11y](https://pa11y.org/): `npx pa11y URL`
- Lighthouse: Chrome DevTools Accessibility tab

## License

MIT
