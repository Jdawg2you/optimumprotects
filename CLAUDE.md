# optimumprotects.com

Client-facing site for Optimum Financial Solutions. Static HTML, no build step.

## How it deploys
- GitHub Pages serves `main` from the repo root. **Push = publish**, live a minute or two later.
- `CNAME` holds `optimumprotects.com`. DNS is at GoDaddy: four `@` A records to
  185.199.108–111.153, `www` CNAME to `jdawg2you.github.io`. HTTPS is enforced.
  Jesse makes DNS changes by hand; Claude is not permitted to edit them.
- Pretty URLs work: `/health` serves `health.html`, `/manhattanlife` serves
  `manhattanlife/index.html`. Local files link with `.html` so they open from disk too.
- Moved off a Netlify drag-and-drop deploy on 2026-09-16. Netlify is no longer used.

## Layout
- `index.html`, `health.html`, `life.html`, `retirement.html` — the main site; shared `styles.css`.
- `manhattanlife/` — client resource page for ManhattanLife policyholders. It is
  self-contained (its own `<style>` block) but deliberately mirrors the main site's
  design: ivory ground, Playfair headings, Inter UI, gold pills, sage bands, rounded
  inset panels, scroll reveals.
- `logo-horizontal.png` — header logo for every page. `logo.png` is the icon only,
  `optimum-globe.png` the faint hero watermark. Source art lives outside the repo in
  `~/Documents/Claude/Projects/Agency Building Project/Brand Assets/`.
- `manhattanlife/jesse-stamm.vcf` — Jesse's contact card, with the photo embedded.
  The page's QR code points at this file's URL.
- `manhattanlife/og-image.png` — 1200x630 link-preview card for texted links.

## Conventions
- Both forms post to FormSubmit (`formsubmit.co` → wealthbuildersgroupllc@gmail.com).
  No host-side form handling, which is why GitHub Pages is enough.
- Carrier facts come from ManhattanLife/vendor material, never memory. CareGuide is
  469-902-2267 and members@cgasaves.com (the 2026 flyer); older sheets show an
  outdated number and services@.
- Long vendor detail goes in a `<details>` expander whose summary says why to open it,
  rather than a modal or a wall of text.
- Client resource pages live in their own subfolder per carrier.

## Gotchas
- If Pages HTTPS ever stalls on the `*.github.io` certificate, clear and re-set the
  Pages custom domain via the API; that triggers issuance and writes two CNAME commits,
  so pull afterwards.
- Preview locally with `python3 -m http.server 8765` from the repo root, then open
  `http://localhost:8765/manhattanlife/`.
