# Frontend Design-Quality Flow

A curated **Flowy** Flow: hand-picked best-of-breed frontend skills + a `FLOW.md` router. Install it and FLOW.md routing makes the right skill fire at each phase of UI work — build the interface with genuine design quality, review the rendered result for visual polish, then audit it for accessibility.

## Install

```
/flowy frontend-design-flow
```

## What it routes

| Phase | Skill | Source |
|---|---|---|
| Build / reshape the UI | `frontend-design` | Anthropic |
| Visual design-quality review | `design-review` | Jezweb |
| Accessibility (WCAG) audit | `accessibility` | Addy Osmani |

Arc: **build → design-review → accessibility**. Building a screen routes to `frontend-design`; once it renders, `design-review` checks whether it looks polished, then `accessibility` audits it against WCAG 2.2. Polishing an existing screen skips the build phase (design-review → accessibility).

## Credits & license

Skills are vendored verbatim from their upstream authors — see [ATTRIBUTION.md](./ATTRIBUTION.md) for per-skill author, license, and source. `frontend-design` is Apache-2.0 (Anthropic); `accessibility` (Addy Osmani) and `design-review` (Jezweb) are MIT. All three are permissive, so **this Flow is licensed MIT as a whole** (see [LICENSE](./LICENSE)); the Apache-2.0 NOTICE for `frontend-design` is reproduced in ATTRIBUTION.md. FLOW.md routing by Flowy.
