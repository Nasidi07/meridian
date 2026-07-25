# Meridian — luxury multi-brand car dealership

A cinematic storefront for a global performance & luxury car dealer. Dark/light
themable, fully responsive, no build step, no dependencies, no photography
(all imagery is generated inline SVG).

## Pages
- `index.html` — home: cinematic hero, quick search, featured inventory, categories, why-us, animated stats, financing calculator, electric collection, testimonials, locations, newsletter
- `inventory.html` — live filters (marque/body/fuel/price/condition/location), sort, grid+list views, compare, active-filter chips, empty state; reads `?marque=`, `?body=`, `?fuel=`, `?max=`
- `vehicle.html?id=<id>` — gallery, spec ribbon, performance triad, spec tables, features, FAQ, financing calculator (live), test-drive booking with validation, related
- `compare.html` — up to 3 side-by-side with best-in-row highlights; supports `?ids=a,b,c`
- `design-system.html` — tokens, type scale, spacing, and the live component library
- `404.html` is not included in this slice (see "What's next")

## Run / deploy
Static files — open `index.html`, or drag the folder onto **vercel.com/new** or
**app.netlify.com/drop**. Locally: `python3 -m http.server` then visit the port.

## Architecture
- `assets/css/tokens.css` — dark + light themes, type scale, spacing, semantic colours
- `assets/css/app.css` — reset, typography, and the full component library
- `assets/js/data.js` — the 16-vehicle catalogue, the cinematic SVG scene generator, card markup, financing math. **Single source of truth** — edit a price here, it updates everywhere.
- `assets/js/app.js` — theme toggle (persisted), nav, wishlist, compare, search, toast, counters, reveal

## Notes on scope
This is the **vertical slice** of a much larger brief: design system + the three
pages that carry the brand and conversion, built deep enough that the rest extend
mechanically from the same tokens, components and data layer.

**What's next, in priority order:** customer dashboard, dealer dashboard, admin
dashboard, dedicated financing & trade-in pages, services, about/contact/blog/FAQ,
auth flows, and a 404. Each reuses `tokens.css`, `app.css`, and the `data.js` layer.

## Imagery & IP
No photography or manufacturer logos are used. Each listing renders a generated
inline-SVG "scene" (atmospheric ground, marque-hued glow, car silhouette, light
sweep, reflection), seeded per vehicle so a car looks the same everywhere. Model
names are referenced as plain text, the way any dealer lists stock.

## Verified
All six pages: one `<h1>` each in Space Grotesk, zero horizontal overflow at
360/768/1024/1440/1920, both themes, no console errors, skip-link first tab stop,
reduced-motion respected, every icon-button labelled. Interactions tested
end-to-end: theme persistence, filters/sort/chips, grid⇄list, compare (cap of 3,
best-in-row, remove, shareable `?ids=`), wishlist drawer, search + no-match state,
both financing calculators, tabs, and booking-form validation.
