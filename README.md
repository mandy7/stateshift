# StateShift — Website v2

A premium coffee journal, not a shop. Paper/parchment base with dark espresso
interludes, built as plain static HTML — no build step, deploys straight to Vercel.

## Pages

| File | URL (after deploy) | Purpose |
|---|---|---|
| index.html | / | Orient + route: buyers → Collection, readers → Journal |
| story.html | /story | Why StateShift exists (autopilot, perfume insight, beliefs) |
| ritual.html | /ritual | The two-sachet system + six brew steps |
| collection.html | /collection | Sehar · Rukh · Kisse · Lamhe (+ Mehfil resting) |
| sampler.html | /sampler | The one conversion page — WhatsApp request |
| journal.html | /journal | Curated founder entries with real experiment photos |
| lab.html | /lab | Raw session log — **reads from lab.json** |
| observations.html | /observations | Before/after charts — **reads from states.json** |
| faq.html | /faq | Honest objection handling |
| contact.html | /contact | WhatsApp / email / Instagram + taster invitation |

## Before you deploy — replace these

1. **WhatsApp number** — search for `91XXXXXXXXXX` in `sampler.html` and
   `contact.html`, replace with your number in international format.
2. **Sampler price** — `₹300` in `sampler.html` is a placeholder based on the
   ₹50/sachet validation. Set the real number.
3. **Email + Instagram** — placeholders in `contact.html`
   (`hello@stateshift.in`, `@stateshiftcoffee`).

## Updating the Lab and Observations

Both pages fetch their JSON at load time — no HTML editing needed:

- `lab.json` — array of session entries (same schema as before:
  id, date, time, title, tags, sku, body, observations[], metrics, note).
- `states.json` — array of before/after rows per session
  (focus/energy/mood for RUKH, warmth/mystery/linger for KISSE).

Add new sessions to the JSON, redeploy, done. Sessions missing a metric are
excluded from that metric's average — not counted as zero (this was a bug in v1).

## Local preview

Browsers block `fetch()` from `file://`, so the Lab/Observations pages need a
tiny server:

    cd "Website v2"
    python3 -m http.server 8000
    # open http://localhost:8000

Everything else works by double-clicking the HTML files.

## Assets

- `assets/site.css` — shared design tokens & components (single source of styling)
- `assets/posters/` — SKU cards + tasting form (from your Posters folder, web-sized)
- `assets/photos/` — 20 curated experiment photos (web-sized, renamed meaningfully)

The old site was left untouched in "Website Git code" for reference.
