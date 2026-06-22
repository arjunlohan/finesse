# finesse

**Design-engineering craft for interfaces that feel polished, fast, and physical** — packaged as an Agent Skill for Claude Code, Cursor, Codex, Gemini CLI, and other skill-aware coding assistants.

Great interfaces are rarely one big thing. They're an accumulation of small, individually invisible details that compound — *felt, not seen*. `finesse` teaches your AI coding assistant those details as concrete, committed defaults: a motion-token system, interaction states, surfaces & depth, typography, layout & color, performance, and accessibility.

## Install

```sh
npx skills add arjunlohan/finesse        # project-scoped
npx skills add arjunlohan/finesse -g     # global: available in every project
```

Once installed it **auto-triggers** on UI / animation / "make it feel better" work, or you can invoke it manually with `/finesse`. Without installing, you can also just point any assistant at [`skills/finesse/SKILL.md`](skills/finesse/SKILL.md).

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
| [`sources.md`](skills/finesse/sources.md) | Who each principle comes from, with links |

## How it's built

- **Framework-agnostic first.** Every technique leads with vanilla CSS / the Web Animations API, then shows Tailwind and Motion (`motion`/`framer-motion`) variants. It won't add an animation dependency that isn't already in your `package.json`.
- **Committed numbers, not vibes.** One motion-token scale (durations + easings + springs) instead of hand-picked values; exact thresholds with the negative case taught alongside ("don't do X, because…").
- **Progressive disclosure.** `SKILL.md` carries every number you need to act; the reference files are pulled in on demand for depth.
- **Accessibility is not optional.** A first-class `prefers-reduced-motion` policy (substitute, don't delete), forced-colors, focus, and contrast are baked in — not bolted on.

## Credits & provenance

`finesse` is an **original** skill — not a fork — but it owes its framing (and the progressive-disclosure packaging) to Jakub Krehel's [make-interfaces-feel-better](https://github.com/jakubkrehel/make-interfaces-feel-better), which it deliberately extends with a motion-token system, accessibility, interaction states, performance, and modern platform primitives.

The defaults are distilled from the people who set the bar — Rauno Freiberg, Emil Kowalski, Vercel Geist, Linear, Stripe, Apple HIG, Material Design, Josh Comeau, Refactoring UI, and others. Full citations in [`skills/finesse/sources.md`](skills/finesse/sources.md). Not affiliated with or endorsed by any of them.

## License

[MIT](LICENSE) © Arjun Lohan
