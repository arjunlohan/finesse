# Embedding the finesse showcase in another site

This folder is a **self-contained showcase**: a dark landing page (`index.html`) that
renders 15 UI components built two ways (with and without the finesse skill), as live,
interactive iframes. Everything is vanilla HTML/CSS/JS with **no build step and no
dependencies**.

## Structure

- `index.html`: the page. It renders the comparison sections from an inline JSON block
  (`<script type="application/json" id="cmp-data">`) and loads each component as an
  `<iframe>`.
- `components/`: 30 self-contained HTML files named `<nn>-<slug>--control.html` and
  `<nn>-<slug>--finesse.html`. `index.html` references them with **relative paths**
  (`components/...`).

## To embed in a portfolio or another site

The page uses full-page styles of its own (its own dark theme, fixed background, scroll
reveal), so the cleanest integration is to **isolate it**. Pick one:

1. **Copy + iframe (recommended).** Copy this entire `showcase/` folder into your site's
   static assets, keeping `index.html` and `components/` together in the same directory.
   Then embed it on your skills page:
   ```html
   <iframe
     src="/skills/finesse/index.html"
     title="finesse: same prompt, with and without the craft"
     style="width:100%; height:100vh; border:0; border-radius:16px;"
     loading="lazy">
   </iframe>
   ```
   The iframe sandboxes the showcase's dark theme and scripts so they never collide with
   your site's CSS.

2. **Standalone route.** Serve `index.html` at a route like `/skills/finesse` and serve
   `components/` as static files alongside it. It is plain static files: no framework
   integration needed.

3. **Link out.** Host the folder (e.g. GitHub Pages) and link to it from your skills page.

## Rules (so it renders correctly)

- Keep `index.html` and `components/` in the **same directory**. The relative
  `components/...` paths must resolve from wherever `index.html` is served.
- Serve over **http(s)** or localhost. `file://` renders the comparisons fine, but the
  hero's copy-to-clipboard button needs a secure context.
- **Do not** run the component files through your bundler or inline them. They are meant
  to load as separate documents in iframes: that separation is what isolates each demo.
- It is already responsive: comparisons sit side by side at ≥1000px and stack below that.
  If you embed it in a narrow column, give the iframe room or let it go full-bleed.

## To feature a different set or reorder

Edit the `cmp-data` JSON in `index.html` (the `DATA` array) and the `FILE` map below it.
All 15 component pairs are in `components/`.
