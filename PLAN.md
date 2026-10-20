# public-lands-data-repo: the founding plan and running record

The United States' **public lands** and the Forest Service's **roads and trails**, as vector tiles. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing is published yet.**

## What it is for

Two products, each a pyramid of Mapbox vector tiles (uncompressed, extent 4096, Web Mercator, the XYZ scheme) with an index naming every tile to zoom 8 and a root naming its version, R2's alone: **`padus`** (`padus.json`, `map/land/padus/`), zooms 4 to 12, one polygon layer `lands` — PAD-US 4.1's Fee and Easement features with their public access code (open, restricted, closed, unknown), manager, manager type, designation and GAP status, each code beside PAD-US's own words for it, the unit's name, the category and the state; and **`usfs-routes`** (`usfs-routes.json`, `map/land/usfs-routes/`), zooms 8 to 13, two line layers: `roads`, the Motor Vehicle Use Map's roads with the vehicle classes each is open to and their dates, and `trails`, the Motor Vehicle Use Map's trails and every National Forest System trail, with the uses each is managed for or accepts. A set's version is its tiles' own hash, so an unchanged rebuild publishes nothing new.

## Where the data comes from

**PAD-US 4.1**, USGS Gap Analysis Project, Protected Areas Database of the United States, published 2025-03-31: public domain, read from USGS's own web service of it (the *PAD-US Manager Name* feature layer view on USGS's ArcGIS Online, which USGS's *PAD-US Web Services* page offers to developers), since the ScienceBase downloads are served only behind a reCAPTCHA. Its caveats travel with it: not a legal boundary; public access assigned largely by designation type; not every area reviewed locally; and, by its use constraints, not to be combined with finer data into hybrid maps — so it is published as USGS publishes it. Citation: U.S. Geological Survey (USGS) Gap Analysis Project (GAP), 2024, Protected Areas Database of the United States (PAD-US) 4.1: U.S. Geological Survey data release, https://doi.org/10.5066/P96WBCHS. **The Forest Service's roads and trails**, its Geodata Clearinghouse (data.fs.usda.gov/geodata/edw/), refreshed weekly: no access constraint; not legal documents, not to determine title, ownership, boundaries, jurisdiction or restrictions; altered downloads shared are to be named as such. Not every National Forest publishes Motor Vehicle Use Map data, and an open date is when a vehicle is legal, not when a road is passable. Terms read 2026-10-20.

## 2026-10-20: the first run, and the schedule

The first dispatched run (`39397801521`, 09:02-10:37 UTC) was green: PAD-US 4.1's 21 state groups tiled four at a time and joined, its zooms 4 to 8 dissolved by class, and the Forest Service's roads and trails from zoom 8 - `land/padus/` and `land/usfs-routes/` on R2 alone, the upload 45 minutes. The schedule set then: daily at 07:41 UTC, PAD-US rebuilt only when USGS's service changes and the routes each month.

## Open

1. Then the daily schedule.
2. A month of runs read: the cache kept warm by the daily restore, the routes rebuilt when their files move.
