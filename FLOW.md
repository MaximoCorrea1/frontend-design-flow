# FLOW.md: Frontend Design-Quality

> Routes frontend UI work so the right skill fires at each phase: build the interface with genuine design quality, review the rendered result for visual polish, then audit it against WCAG for accessibility.
> Skills vendored from Anthropic (Apache-2.0), Jezweb (MIT), and Addy Osmani (MIT) — see ATTRIBUTION.md. Routing by Flowy.

<!-- The Flowy engine supplies the universal contract (announce ritual, invoke/READ,
     host-wins, post-compaction re-read). This file carries only the routing. -->

## Phases

1. **Build** — entry: a UI to create or reshape (page, component, app, design system). Gate: a screenshot self-critique done before declaring the build done.
2. **Design review** — entry: a rendered UI exists, judge how it looks. Gate: a written findings report (layout, spacing, hierarchy, consistency) with screenshots.
3. **Accessibility** — entry: the visual pass is settled, prove it works for everyone. Gate: every WCAG 2.2 issue (contrast, keyboard, screen-reader, focus) triaged before declaring done.

## Routing

```
USER MESSAGE RECEIVED
│
├─ INTAKE / TRIAGE  (always first)
│   └─ new frontend request or first message — which phase does it land in?
│       → invoke frontend-design
│       Gate: a concrete subject + the page's single job named before any pixels
│
├─ BUILD  (entry: a UI to create or reshape)
│   ├─ "build a page / component / dashboard / landing page"?
│   │   → invoke frontend-design
│   │   Gate: a screenshot self-critique before the build is called done
│   └─ "reshape / restyle this existing screen"?
│       → invoke frontend-design
│       Gate: before/after screenshots; the change tied to a stated design intent
│
├─ DESIGN REVIEW  (entry: a rendered UI exists, judge how it looks)
│   ├─ "does this look good? / review the design / is it polished?"
│   │   → invoke design-review
│   │   Gate: a written findings report (layout, spacing, hierarchy, consistency) with screenshots
│   └─ "it looks off but I can't say why / check the visual quality"?
│       → invoke design-review
│       Gate: each visual finding recorded with a before screenshot
│
├─ ACCESSIBILITY  (entry: the visual pass is settled)
│   ├─ "a11y audit / WCAG / contrast / keyboard / screen reader"?
│   │   → invoke accessibility
│   │   Gate: every WCAG 2.2 issue triaged (contrast, keyboard, focus, SR) before done
│   └─ "make it accessible / can everyone use this?"?
│       → invoke accessibility
│       Gate: the a11y findings ranked by severity before any "done" claim
│
├─ DONE-CHECK / VERIFY  (before any "looks done" or "shipped" claim)
│   └─ about to claim the UI is finished or looks right?
│       → invoke design-review
│       Gate: the rendered result re-screenshotted and checked against the findings before the claim
│
├─ ADVISE-ONLY  (asking me to advise / explain, not to build)
│   └─ "should I…? / explain how X affects the design"?
│       → answer only; do not start a phase
│       Gate: (soft) advice given; Routing: none
│
├─ SCOPE CHANGE  (a new screen or new target mid-stream)
│   └─ the brief changed after a build or review started?
│       → re-enter BUILD for the new target
│       Gate: the new screen's build intent restated before reviewing it
│
├─ BLOCKED  (waiting on copy, assets, an API, or a design decision)
│   └─ cannot build or review until something external lands?
│       → park; do not fake a screen or invent content
│       Gate: the blocker named, the resume condition set
│
├─ REVIEW-LOOP  (feedback came back on the UI)
│   └─ a design change came back for re-review?
│       → invoke design-review
│       Gate: the after-screenshot re-checked; no visual regression introduced
│
└─ DEFAULT / NO-MATCH  (always last)
    └─ nothing above fits this message?
        → answer only; ask one scoping question
        Gate: (soft) Routing: none — ask, do not guess
```

## Priority on collision

When more than one leaf could fire on the same message, resolve in this order:

1. **Blocked / waiting on external** — surface a known blocker (missing copy, asset, API) before starting new work.
2. **Scope changed** — a new screen or target invalidates the old build; re-enter Build first.
3. **Done-check / verify** — any "it looks done / shipped" claim runs design-review before the claim leaves your mouth.
4. **Build before review** — `frontend-design` produces the interface; `design-review` and `accessibility` assess what it rendered. You cannot review a screen that does not exist yet.
5. **Looks before a11y** — a visual pass (`design-review`) precedes the `accessibility` audit; fix obvious layout and hierarchy breakage before measuring contrast and focus order on a moving target.
6. **Advisory** — a pure "explain / should I" question answers without starting a phase.
7. **Default / no-match** — loses to everything; fires only when nothing else matches.

## You are rationalizing if you think…

- "Just build it, the design will sort itself out." → Name the subject and the page's one job first. An unanchored build defaults to templated slop.
- "It renders, so it's done." → Design review. Screenshot it and judge layout, spacing, and hierarchy before the "done" claim.
- "It looks fine, accessibility can wait." → Audit. Contrast, keyboard order, and focus management are not optional polish; they decide who can use it.
- "I know which phase I am in after compaction." → Re-read this file and restate the phase before continuing.

## Attribution

- `frontend-design` by **Anthropic** (https://github.com/anthropics/skills), Apache-2.0 (NOTICE preserved in ATTRIBUTION.md).
- `design-review` by **Jezweb / Jeremy Dawes** (https://github.com/jezweb/claude-skills), MIT.
- `accessibility` by **Addy Osmani** (https://github.com/addyosmani/web-quality-skills), MIT.
- FLOW.md routing by **Flowy**, MIT. The vendored skills keep their own licenses; the Flow bundle as a whole is MIT (see LICENSE + ATTRIBUTION.md).
