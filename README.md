# finesse

[![npx skills add arjunlohan/finesse](https://img.shields.io/badge/npx%20skills%20add-arjunlohan%2Ffinesse-111?style=flat-square)](#install) [![Stars](https://img.shields.io/github/stars/arjunlohan/finesse?style=flat-square&color=111)](https://github.com/arjunlohan/finesse/stargazers) [![License: MIT](https://img.shields.io/badge/license-MIT-111?style=flat-square)](LICENSE)

**Design-engineering craft for interfaces that feel polished, fast, and physical**: packaged as an Agent Skill for Claude Code, Cursor, Codex, Gemini CLI, and other skill-aware coding assistants.

Great interfaces are rarely one big thing. They're an accumulation of small, individually invisible details that compound: *felt, not seen*. `finesse` teaches your AI coding assistant those details as concrete, committed defaults: a motion-token system, interaction states, surfaces & depth, typography, layout & color, performance, and accessibility.

## Install

```sh
npx skills add arjunlohan/finesse        # project-scoped
npx skills add arjunlohan/finesse -g     # global: available in every project
```

Once installed it **auto-triggers** on UI / animation / "make it feel better" work, or you can invoke it manually with `/finesse`. Without installing, you can also just point any assistant at [`skills/finesse/SKILL.md`](skills/finesse/SKILL.md).

## What it changes, in one diff

Same prompt ("add a hover state to this card"), same assistant, with and without the skill loaded.

**Before**

```css
.card { transition: all 0.3s ease; }
.card:hover { transform: scale(1.05); box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3); }
```

**After**

```css
:root {
  --duration-fast: 150ms;                      /* micro: hover, press, color */
  --ease-standard: cubic-bezier(0.2, 0, 0, 1); /* small in-place state changes */
}

.card {
  transition:
    transform   var(--duration-fast) var(--ease-standard),
    box-shadow  var(--duration-fast) var(--ease-standard);
}

.card:hover {
  transform: translateY(-2px);
  box-shadow: 0 1px 2px rgb(0 0 0 / 0.06), 0 8px 24px rgb(0 0 0 / 0.10);
}

@media (prefers-reduced-motion: reduce) {
  .card { transition-duration: 1ms; }
  .card:hover { transform: none; }
}
```

Four things changed and none of them were a judgement call: named tokens instead of hand-picked numbers, compositor-only properties instead of `all`, easing chosen by the direction of travel, and a reduced-motion path that substitutes rather than deletes.

## What it covers

| File | Covers |
| --- | --- |
| [`SKILL.md`](skills/finesse/SKILL.md) | The spine: the motion-token system, core principles, common mistakes, a review/output contract + checklist |
| [`motion.md`](skills/finesse/motion.md) | Duration/easing/spring tokens, enter/exit, interruptibility, origin, stagger, when-not-to-animate, modern primitives (View Transitions, `@starting-style`, scroll-driven) |
| [`interaction-states.md`](skills/finesse/interaction-states.md) | Hover/active/focus-visible/disabled, loading & skeletons, empty/error states, optimistic UI, menus |
| [`surfaces.md`](skills/finesse/surfaces.md) | Concentric radius, shadows vs borders & elevation, image outlines, optical alignment, hit areas |
| [`typography.md`](skills/finesse/typography.md) | Wrapping, smoothing, tabular numbers, hierarchy, measure, line-height, fluid sizing |
| [`layout-and-color.md`](skills/finesse/layout-and-color.md) | Spacing & grouping, alignment, near-black/white, functional color scales, depth |
| [`performance.md`](skills/finesse/performance.md) | Compositor-only animation, `will-change`, FLIP, the tool ladder, 60fps/RAIL, perceived speed |
| [`accessibility.md`](skills/finesse/accessibility.md) | `prefers-reduced-motion` policy, forced-colors, contrast, focus, semantics & ARIA |

## How it's built

- **Framework-agnostic first.** Every technique leads with vanilla CSS / the Web Animations API, then shows Tailwind and Motion (`motion`/`framer-motion`) variants. It won't add an animation dependency that isn't already in your `package.json`.
- **Committed numbers, not vibes.** One motion-token scale (durations + easings + springs) instead of hand-picked values; exact thresholds with the negative case taught alongside ("don't do X, because…").
- **Progressive disclosure.** `SKILL.md` carries every number you need to act; the reference files are pulled in on demand for depth.
- **Accessibility is not optional.** A first-class `prefers-reduced-motion` policy (substitute, don't delete), forced-colors, focus, and contrast are baked in: not bolted on.

## License

[MIT](LICENSE) © Arjun Lohan
