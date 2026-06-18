# FLOW.md: Frontend Design-Quality

> Routes a curated set of frontend-design skills so the right one fires at each phase of UI work: build the interface with real design quality, review the rendered result for visual polish, then audit it for accessibility.
> Skills vendored from Anthropic (Apache-2.0), Addy Osmani (MIT), and Jezweb (MIT) — see ATTRIBUTION.md. Routing by Flowy.

<!-- The Flowy engine supplies the universal contract (announce ritual, invoke/READ,
     host-wins, post-compaction re-read). This file carries only the routing. -->

## Routing

```
USER MESSAGE
  ├─ building or reshaping UI — a page, component, app, or design system?  → invoke frontend-design   gate: screenshot self-critique before "done"
  ├─ does it LOOK good? visual polish / layout / spacing / hierarchy pass? → invoke design-review      gate: findings report w/ screenshots
  ├─ is it accessible? WCAG / a11y / screen-reader / keyboard audit?       → invoke accessibility      gate: WCAG issues triaged before "done"
  └─ question, not frontend work?                                          → answer only; no skill
```

## Priority on collision

When more than one branch matches, resolve top-down:

1. **Build before review**: `frontend-design` produces the interface; `design-review` and `accessibility` assess what it rendered. You cannot review a screen that does not exist yet.
2. **Looks before a11y**: a visual-quality pass (`design-review`) precedes the `accessibility` audit — fix obvious layout/hierarchy breakage before measuring contrast and focus order on a moving target.
3. Otherwise lifecycle order: build → design-review → accessibility.

## Phases

1. **Build**: frontend-design. Generate or reshape the UI with intentional composition, typography, color, and motion. Gate: a screenshot self-critique before declaring done.
2. **Design review**: design-review. Review the rendered page for visual quality — layout, spacing, color, hierarchy, consistency, responsive behavior. Gate: a written findings report with screenshots.
3. **Accessibility**: accessibility. Audit against WCAG 2.2 — contrast, keyboard navigation, screen-reader support, focus management. Gate: every WCAG issue triaged before declaring done.

**Shortcut:** polishing an existing screen (no new build) → design-review → accessibility (skip the build phase).

## Attribution

- `frontend-design` by **Anthropic** (https://github.com/anthropics/skills), Apache-2.0.
- `accessibility` by **Addy Osmani** (https://github.com/addyosmani/web-quality-skills), MIT.
- `design-review` by **Jezweb** (https://github.com/jezweb/claude-skills), MIT.
- FLOW.md routing by **Flowy**. All vendored skills are MIT or Apache-2.0 (both permissive); the Flow bundle as a whole is licensed **MIT** — see LICENSE + ATTRIBUTION.md (Apache-2.0 NOTICE for `frontend-design`).
