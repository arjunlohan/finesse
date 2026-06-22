# finesse — showcase

A self-contained landing page that proves what the `finesse` skill is worth, by experiment.

**The method:** 15 UI components, each built **twice** by Opus 4.8 at extra-high effort with the same prompt. The only variable was whether the agent read the finesse skill first. The page shows all 15 side by side as live, interactive iframes (`Opus 4.8` vs `Opus 4.8 + /finesse`).

## Run it

```sh
cd showcase
python3 -m http.server 8000   # → http://localhost:8000
```

(`file://` works too, except the hero's copy-to-clipboard button needs http/localhost.)

## Structure

```
showcase/
  index.html     the page (self-contained: inline CSS/JS, no dependencies)
  components/    30 files: <nn>-<slug>--{control,finesse}.html, each loaded as an iframe
  EMBED.md       how to drop this into another site or portfolio
```

The page itself is built to finesse spec (motion tokens, direction-correct easing,
`:focus-visible` rings, dark-mode ring elevation, `prefers-reduced-motion`,
velocity-aware reveal). It dogfoods the skill it is showing off.

## Embed it elsewhere

See [`EMBED.md`](EMBED.md) — it is written so a coding agent can follow it directly.

## Feature a different set or reorder

Edit the `cmp-data` JSON block in `index.html` (the `DATA` array — each entry has
`file`, `cat`, `headline`, `tell`, `try`, `prompt`, `h`) and the `FILE` map just below
it in the script. All 15 component pairs live in `components/`.
