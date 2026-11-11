# Ecosystem

A source-backed startup ecosystem explorer built with Next.js, React and TypeScript. A useful starting point for finding partners, programs and entry routes, with the uncertainty left visible.

## Explore

- Editorial landing page with a navigable ecosystem illustration.
- Full-text search across names, benefits, eligibility, regions and retained research.
- Type and category filters, shareable URL state, explicit load-more and browser-history restoration.
- Interactive category map, detail pages, linked sources and researched record connections.
- Versioned JSON data and downloadable catalog. No database account, credentials, billing or external search service required.
- Responsive layouts, keyboard controls, reduced motion, automated accessibility checks and a custom 404.

## Dataset

| Records                      | Count | Meaning                                                                   |
| ---------------------------- | ----: | ------------------------------------------------------------------------- |
| Partners                     |   183 | Names observed in a supplied directory, not verified current partnerships |
| Program / entry-route groups |    46 | Research summaries, sometimes covering multiple tiers or routes           |
| Ventures                     |     0 | Supported by the schema, intentionally empty until sourced                |
| Entry-route connections      |    18 | Source-evidenced research connections, not commercial affiliations        |

The source research is dated **November 11, 2026**. Imported check dates are not fresh independent verification. Original Space citations require access; public source links are retained where available. Private application state and personal qualification strategy are excluded.

**Start with the [ecosystem map and complete index](docs/ECOSYSTEM_MAP.md)**, [data model](docs/DATA_MODEL.md) and [source inventory](docs/SOURCES.md).

## Run locally

Use Node.js 24 LTS (Node.js 22.13+ also supports the unit-test runner) and npm.

```bash
npm ci
npm run dev
```

Open http://localhost:3000.

## Validate and build

```bash
npm run check
npm run test:e2e
```

The `check` script regenerates and validates the catalog, then runs lint, typecheck, unit tests and production build. `test:e2e` expects a completed build and starts its own static server. It uses `/usr/bin/chromium` by default; set `CHROMIUM_PATH` to your Chrome/Chromium executable. Python 3 is used only for the local static preview server, not by the app itself.

```bash
npm run build
npm run preview
```

Next.js exports the site to `out/`. All 229 detail routes are pre-rendered. Search and filters run locally in the browser; editing data requires a repository change and rebuild.

## Deployment state

This repository started empty with no configured hosting integration or release path. No deployment, hosted database, DNS change, new account or paid resource is created by this implementation. Deploy the generated `out/` directory through an approved static hosting path, or configure a Next.js-compatible build with `npm ci && npm run build` and output directory `out`.

Serve nested routes through their `index.html` files and configure unknown paths to use `404.html`. Do not use an SPA fallback to the landing page. `trailingSlash` is enabled for portable static hosting.

## Project map

```text
src/app/                Landing, explore, about, record detail and 404 routes
src/components/         Shared chrome, cards, explorer and category map
src/lib/                Typed catalog and pure search/URL helpers
data/                   Canonical versioned records and retained source research
public/data/            Generated portable download
scripts/                Validation and repository-index generation
tests/                  Unit, workflow and accessibility coverage
docs/                   Generated map, source inventory and data model
DESIGN.md               Visual tokens and component ownership
UX-CONTRACT.md          Search, evidence and navigation behavior
```

No scraping, authentication, submission forms or automatic program-eligibility decisions are implemented. Updating the source catalog is an explicit, reviewable data operation.
