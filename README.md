# SRIR Book website

Static site for GitHub Pages: plain HTML/CSS, no build step.

- `index.html` – landing page with link tiles (styles in `style.css`)
- `sr-facilities-worldwide.html` – interactive map of synchrotron radiation facilities (self-contained; Plotly is embedded, the detailed 1:50m outlines load from cdn.plot.ly when zooming in)

## Local preview

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.
