# Periplum map template

A starting point for your own **[Periplum](https://github.com/periplum/periplum)** history
map — a chronological route of placed points on Earth, the Moon, Mars, or the sky.

## Make your own map (5 steps)

1. Click **“Use this template” → Create a new repository**.
2. Edit **`index.html`** — set the `title`, `repo`, `statusColors`, and `basemaps`
   (Earth tiles by default; add a Moon/Mars/celestial basemap to get a basemap switcher).
3. Edit **`data.json`** — your chronological `items`, each with one or more `placements`
   (`lat`/`lon` for tile/image basemaps, `ra`/`dec` for celestial). See the contract in the
   [engine README](https://github.com/periplum/periplum-core#data-contract).
4. **Settings → Pages →** deploy from `main` / root. Your map is live at
   `https://OWNER.github.io/REPO/`.
5. *(Optional, for evolving datasets)* add a `source.py` that prints the canonical JSON,
   and keep `.github/workflows/refresh-data.yml`.

## What's in here

| File | Purpose |
| --- | --- |
| `index.html` | The whole app: loads the pinned Periplum engine from jsDelivr + your config |
| `data.json` | Your data (canonical Periplum contract) |
| `.github/workflows/upgrade-periplum.yml` | Auto-opens a PR when a newer engine version ships |
| `.github/workflows/refresh-data.yml` | Re-runs `source.py` on a schedule and PRs data changes |

## Auto-update cadence

- **Engine upgrades** (`upgrade-periplum.yml`) — monthly check is fine; it only acts when a
  new release exists.
- **Data refresh** (`refresh-data.yml`) — match it to your dataset. Slow ones (World Cup,
  Olympics) should run **at most once a year**; for static maps (a finished voyage), just
  delete the workflow.

Both workflows open **pull requests** (never push to `main`), so every change is reviewed.
