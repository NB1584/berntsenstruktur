# Berntsen Struktur

Landing page for **berntsenstruktur.no** – consulting site for structuring ideas, projects and businesses before risk.

## Tech

- Static HTML, CSS, minimal JavaScript
- Hosted on GitHub Pages (custom domain via `CNAME`)
- No build step; no frameworks

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
# Python
python -m http.server 8000

# Node (npx)
npx serve
```

Then visit `http://localhost:8000`.

## Structure

- `index.html` – markup and content
- `styles.css` – all styles
- `script.js` – smooth scroll for anchor links
- `assets/` – images, favicon (add when needed)

See [ARCHITECTURE.md](ARCHITECTURE.md) for the full structure and [IMPROVEMENTS.md](IMPROVEMENTS.md) for suggested next steps.
