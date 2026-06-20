# RenderWorks — Silicone Render SEO Implementation Package

Production-ready re-engineering of `/services/silicone-render.html` (commercial/transactional intent) to an answer-first, entity-dense, AI-Overview-citable spec. Drop-in for the existing GuildfordGates-framework site.

## Files
| File | Purpose |
|---|---|
| `silicone-render.FULL.html` | Complete standalone page (head + nav + body + schema). References `/css/site.css`. |
| `silicone-render.head.html` | `<head>` fragment (title, meta, canonical, OG). |
| `silicone-render.body.html` | `<main>` fragment + inline calculator/FAQ JS. Paste into an existing template. |
| `silicone-render.schema.jsonld.html` | JSON-LD `@graph` — paste before `</body>`. |
| `robots.txt` | Site root. |
| `sitemap.xml` | Site root. |
| `_preview.html` | Local-preview copy (CSS path points at `../renderworks-gg/`). Not for production. |

## Integration (2 routes)
**A — replace the page:** publish `silicone-render.FULL.html` as `/services/silicone-render.html`. Replace `{{DOMAIN}}` etc. first.
**B — merge into your generator:** drop the `<main>…</main>` from `.body.html` into the existing page, add the `.head.html` meta, and the `.schema.jsonld.html` block before `</body>`. This keeps your real nav/footer.

Then: deploy `robots.txt` and `sitemap.xml` to the web root, and submit the sitemap in Google Search Console.

## Placeholder checklist (MUST replace before publishing)
- [ ] `{{DOMAIN}}` — production hostname
- [ ] `{{PHONE}}` — tracked phone (currently the demo `01483 000 000`)
- [ ] `{{NAP_ADDRESS}}` / `{{POSTCODE}}` — registered address (LocalBusiness needs a real NAP; must match Google Business Profile exactly)
- [ ] `{{RATING}}` / `{{REVIEW_COUNT}}` — live Google rating + count. **Must mirror the Business Profile. If you can't show on-page reviews that match, delete the `aggregateRating` object** — mismatched/unverifiable ratings are a structured-data violation and a manual-action risk.
- [ ] `{{GBP_CID}}` — Google Business Profile URL for `sameAs`
- [ ] `{{COMPANY_NO}}` — Companies House number (optional, in README only)
- [ ] `{{PRICE_UPDATED}}` — date you last verified the £/m² figures (used in `dateModified`, sitemap `lastmod`, calculator, delta block)
- [ ] `{{ENTER_TREND}}` — real scaffold/material cost trend in the delta block
- [ ] Calculator rates `LOW=60 / HIGH=120` — confirm these match prices you will actually honour
- [ ] Hero/OG image files at `/img/…`

## What this package does (and what it deliberately does NOT do)
Built to the parts of the brief that genuinely affect rankings:
- **Answer-first structure** — every H2/H3 is a real query; the first 1–2 sentences are an isolated, SVO, data-bold answer capsule (good for featured snippets / AI Overview extraction).
- **Entity coverage** — silicone-resin / hydrophobic / vapour-permeable / mesh / beads / K-Rend / Weber / EWI / BBA / Article 4, woven as subject–attribute–value prose. `about`/`mentions` link to **real, verified Wikidata QIDs + Wikipedia articles**.
- **Transactional UX** — a working cost calculator top-of-page + sticky quote CTAs to lift genuine engagement and conversions.
- **Valid technical layer** — JSON-LD validates (`@graph`: WebPage, Service, LocalBusiness, BreadcrumbList, FAQPage), `robots.txt`, and a sitemap with honest `lastmod`.

Intentionally omitted, because they don't work as the brief implied and can do harm:
- **No "NavBoost/CrUX-forcing" markup.** Those are measured from real Chrome/user interaction data; no HTML or schema can manufacture them. The calculator earns the signal honestly instead.
- **No fake "crawl-priority verification" meta tags.** Google has no such directive and ignores invented ones. Crawl priority comes from internal links, sitemap `lastmod`, and site speed.
- **No keyword/EAV stuffing past readability.** Over-dense entity repetition trips the helpful-content and spam classifiers — the opposite of the goal. Density here stops at the point a knowledgeable human still reads naturally.
- **No invented facts, prices, ratings, or QIDs.** Everything quantitative is either a verifiable industry figure or a flagged placeholder for you to fill. Shipping fabricated review counts or rates is the fastest route to a manual action.

## Page-speed / CrUX note
The genuine Core Web Vitals levers on this template: serve images as sized WebP/AVIF with width/height attributes, `font-display:swap` (already set), and keep the calculator JS inline (already done, no blocking request). No further action needed for LCP/CLS beyond real images.
