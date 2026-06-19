---
name: frontend-design-flow
description: Build UI that looks good and works for everyone: design with polish, review how it renders, then check accessibility.
version: 0.1.0
license: MIT
domain: frontend
---

# Frontend Design Flow

A curated **Flowy** Flow: hand-picked best-of-breed frontend skills, wired into a `FLOW.md` router that fires the right one at each phase. Build the interface with genuine design quality, review the rendered result for visual polish, then audit it against WCAG for accessibility — build, review, audit, in that order.

## Attribution

The skills in `skills/` are not Flowy's work. They are by:

- **Anthropic** — `frontend-design` (from [anthropics/skills](https://github.com/anthropics/skills), Apache-2.0; NOTICE preserved in ATTRIBUTION.md).
- **Jezweb (Jeremy Dawes)** — `design-review` (from [jezweb/claude-skills](https://github.com/jezweb/claude-skills), MIT).
- **Addy Osmani** — `accessibility` (from [web-quality-skills](https://github.com/addyosmani/web-quality-skills), MIT).

What Flowy added: the `FLOW.md` routing layer. See [ATTRIBUTION.md](./ATTRIBUTION.md) for per-skill license + source + vendored SHA, and [LICENSE](./LICENSE) for the bundle license (MIT).

## How to use

Run `/flowy:frontend-design-flow` to activate. The Flowy hook then enforces FLOW.md routing for the rest of the session, with no manual setup. (`/flowy:frontend-design-flow status` to verify; `/flowy:frontend-design-flow deactivate` to turn off.)
