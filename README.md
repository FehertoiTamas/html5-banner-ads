# HTML5 Banner Ad Portfolio

Five self-contained HTML5 display ads, each a different concept and a
different standard IAB size, built with **GSAP** and a standard
**clickTag** implementation.

| Folder               | Size    | Format name      | Concept                         |
| -------------------- | ------- | ---------------- | ------------------------------- |
| `pulse-300x250/`     | 300×250 | Medium Rectangle | Deep-focus timer app            |
| `ecobrew-728x90/`    | 728×90  | Leaderboard      | Sustainable coffee subscription |
| `northline-160x600/` | 160×600 | Wide Skyscraper  | Outdoor & hiking gear           |
| `fintra-320x50/`     | 320×50  | Mobile Banner    | Budgeting / fintech app         |
| `aroe-300x600/`      | 300×600 | Half Page        | Minimalist furniture brand      |

Each folder is fully independent — one `index.html` with all markup,
CSS, and JS inlined, exactly as an ad network expects a creative to
be packaged (a `.zip` per size, with `index.html` as the entry point).

## Shared conventions across all five

- **`<meta name="ad.size" ...>`** on every file, matching its exact
  pixel dimensions.
- **`clickTag`** — every banner reads `window.clickTag` (injected by
  an ad server at serve time) and falls back to a `FALLBACK_URL`
  constant near the top of the file if none is present, so each one
  also works standalone (e.g. on GitHub Pages).
- **Bounded animation** — each GSAP timeline plays a full entrance
  sequence, repeats twice more (3 plays total), then holds on a
  resting frame, rather than looping forever.
- **No shared assets** — fonts (Google Fonts) and GSAP are pulled
  from CDNs per file; nothing references another folder in this repo,
  since a real ad server will only ever receive one folder's zip at
  a time.

## Trying them locally / on GitHub Pages

1. Push this repo to GitHub and enable **GitHub Pages** (Settings →
   Pages → deploy from the branch).
2. Open any banner directly, e.g.
   `https://yourname.github.io/banner-ads/pulse-300x250/`
3. Append `?clickTag=https://example.com` to any banner's URL to test
   how it behaves when an ad server injects a real destination.

## Customizing

- Each `index.html` has its own `FALLBACK_URL` near the top — point
  it at your CV, portfolio, or LinkedIn.
- Color tokens are declared as CSS custom properties at the top of
  each `<style>` block for quick re-theming.

## Why five different concepts (not five sizes of one ad)

Real ad-tech work usually means adapting to whatever format a
publisher's ad slot demands, and building creative that actually
fits its footprint (a 320×50 mobile banner needs an entirely
different layout approach than a 300×600 half page). Five distinct
briefs, each solved for its own canvas, is a closer approximation
of that job than one design resized five times.
