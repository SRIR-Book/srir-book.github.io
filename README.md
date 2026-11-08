# SRIR Book website

Static site for GitHub Pages (https://srir-book.github.io/): plain HTML/CSS/JS, no build step.

## Pages

- `index.html` – landing page with link tiles (styles in `style.css`)
- `facilities-worldwide.html` – **Accelerator Atlas**: interactive map of synchrotron
  storage rings and free-electron lasers, built with [MapLibre GL JS](https://maplibre.org/)
  6.16 (loaded from jsDelivr)
  - Mercator (Arctic to Antarctic Circle) or globe; world overview from MapLibre's demo
    style, street map from [OpenFreeMap](https://openfreemap.org/) when zoomed in past country level
  - markers: simple (pins) or fancy (ring markers for storage rings, laser pointers for FELs),
    colored by status, optional scaling by ring diameter / FEL length, infrared highlight
  - overlapping markers are grouped with a count badge; click a pin for its website and Wikipedia links
  - downloads: the facility data (zip) and a PNG image (2000 px on the shorter side)

## Data

One facility per line, GeoJSON, edit these to add or correct facilities:

- `data/facilities.geojson` – storage rings: `name`, `city`, `country`, `status`
  (`operating` / `planned` / `decommissioned`), `energy_GeV`, `circumference_m`, `url`,
  `wikipedia` (the facility's article, or its host institution's when it has none), `srir`
- `data/free-electron-lasers.geojson` – FELs: same fields, plus `length_m` and `band`
  (photon range) instead of `circumference_m`

`srir: true` marks facilities offering infrared (an IR beamline, or an IR/THz FEL);
they stay bright with "Highlight infrared".

## Local preview

The map loads its data with `fetch()`, so serve the folder instead of opening the files directly:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
