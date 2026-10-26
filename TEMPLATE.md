# Demo site template (default for all new batches) — v2 "premium"

**Builder:** `python3 build.py batchN_data.json` (uses `template.py` → `page(s)`).
Writes `./<slug>/index.html` and `/tmp/demos/<slug>/index.html` (clone of lucasmcnamara-173/demos).
Then: `cd /tmp/demos && git add -A && git -c user.name=lucasmcnamara-173 -c user.email=lucasmcnamara-173@users.noreply.github.com commit -m "..." && git push`,
wait ~1 min, verify each `https://lucasmcnamara-173.github.io/demos/<slug>/` returns 200 before emailing.
Do NOT run gen_all.py (overwrites prospects.csv). Old gen.py / gen_batch2.py / batch3_build.py are legacy.

**Data fields per prospect (JSON list):** slug, name, cat, city, st, phone, email, src, rev, services[], tag, broken.
Use only the business's real public info. `tag` should come from their own bio/listing. `rev` only if real (e.g. "Nextdoor Neighborhood Favorite in 2024").
Never invent reviews, testimonials, awards, years, license numbers, or hours (template says "call to schedule").

**Art direction:** auto-picked from cat/services in `ART` (handyman, cleaning, landscape, paint, pet, appliance, auto, tile, pressure):
accent/deep/cream palette, display font (Fraunces or Space Grotesk, self-hosted in assets/fonts, OFL), hero image.
Per-service icon + copy from `SV` keyword list. Add a new industry by adding an ART entry + image.

**Images:** `assets/img/<key>.webp` (1024w) and `<key>-sm.webp` (640w), generic AI-generated scenes (no real business, people faces, logos). Labeled "Example photo"; footer says photos are illustrative stock.
Copy `assets/` to `/tmp/demos/assets/` if you add any.

**Sections:** sticky glass header w/ click-to-call, full-bleed hero (Ken Burns), featured+grid services, why-us (dark), 3-step process, gallery, service area + Google Maps embed + contact, FAQ accordion, CTA band with demo form (does not send), footer with discreet "Demo concept" note, mobile bottom Call/Quote bar. Scroll reveals respect prefers-reduced-motion.

**Checks (2026-10-26):** Lighthouse mobile (local) perf 95–97, a11y 100, best-practices 96. SEO 66 only because repo robots.txt disallows indexing (intentional for demos).

## Email
For HTML emails with the inline preview, see COLD_EMAIL_HTML.md. Make the previews with `python3 make_previews.py batchN_data.json` (serve /tmp/demos first: `cd /tmp/demos && python3 -m http.server 8811 &`; prev.js and shot.js are copied here and need puppeteer-core in /tmp/pw, installed with `npm i puppeteer-core`).
