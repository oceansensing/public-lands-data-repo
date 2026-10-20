# public-lands-data-repo

The United States' **public lands** and the Forest Service's **roads and trails**, as vector tiles: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Publishing since 2026-10-20**, daily at 07:41 UTC, PAD-US rebuilt only when USGS's service changes and the routes each month. `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

Two products, each a pyramid of Mapbox vector tiles (uncompressed, extent 4096, Web Mercator, the XYZ scheme) with an index naming every tile to zoom 8 and a root naming its version, R2's alone: **`padus`** (`padus.json`, `map/land/padus/`), zooms 4 to 12, one polygon layer `lands` — PAD-US 4.1's Fee and Easement features with their public access code (open, restricted, closed, unknown), manager, manager type, designation and GAP status, each code beside PAD-US's own words for it, the unit's name, the category and the state; and **`usfs-routes`** (`usfs-routes.json`, `map/land/usfs-routes/`), zooms 8 to 13, two line layers: `roads`, the Motor Vehicle Use Map's roads with the vehicle classes each is open to and their dates, and `trails`, the Motor Vehicle Use Map's trails and every National Forest System trail, with the uses each is managed for or accepts. A set's version is its tiles' own hash, so an unchanged rebuild publishes nothing new.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

**PAD-US 4.1**, USGS Gap Analysis Project, Protected Areas Database of the United States, published 2025-03-31: public domain, read from USGS's own web service of it (the *PAD-US Manager Name* feature layer view on USGS's ArcGIS Online, which USGS's *PAD-US Web Services* page offers to developers), since the ScienceBase downloads are served only behind a reCAPTCHA. Its caveats travel with it: not a legal boundary; public access assigned largely by designation type; not every area reviewed locally; and, by its use constraints, not to be combined with finer data into hybrid maps — so it is published as USGS publishes it. Citation: U.S. Geological Survey (USGS) Gap Analysis Project (GAP), 2024, Protected Areas Database of the United States (PAD-US) 4.1: U.S. Geological Survey data release, https://doi.org/10.5066/P96WBCHS. **The Forest Service's roads and trails**, its Geodata Clearinghouse (data.fs.usda.gov/geodata/edw/), refreshed weekly: no access constraint; not legal documents, not to determine title, ownership, boundaries, jurisdiction or restrictions; altered downloads shared are to be named as such. Not every National Forest publishes Motor Vehicle Use Map data, and an open date is when a vehicle is legal, not when a road is passable. Terms read 2026-10-20.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: none it depends on.

**Which document gets what, and what "update docs" means across all
thirty-one repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all thirty-one, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
