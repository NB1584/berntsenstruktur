# Architecture proposal – Berntsen Struktur

This document proposes a clearer project structure **before** any code changes. Implement only after review.

---

## 1. Current state

| Item | Status |
|------|--------|
| **Entry point** | Single `index.html` |
| **CSS** | Inline in `<style>` (~150 lines) |
| **JavaScript** | None |
| **Assets** | None (no images/icons) |
| **Project map** | Expects `styles.css`, `script.js`, `assets/` – not present |

**Pros:** One file, no requests, trivial to deploy.  
**Cons:** HTML is long and harder to maintain; CSS can’t be cached separately; structure doesn’t match project-map.

---

## 2. Proposed file structure

```
berntsenstruktur/
├── index.html          # Markup only; links to styles.css, optional script.js
├── styles.css          # All site CSS (moved out of index.html)
├── script.js           # Optional; empty or minimal (e.g. smooth scroll, CTA tracking)
├── assets/             # Optional; for images, favicon, icons
│   └── (empty or favicon.ico, etc.)
├── ARCHITECTURE.md     # This document
├── README.md
├── CNAME
├── .gitattributes
└── .cursor/
    └── (unchanged)
```

**Principles:**

- **No build step** – plain HTML/CSS/JS, deploy as-is (e.g. GitHub Pages).
- **No frameworks** – no React/Vue, no npm unless you later add a clear need.
- **Minimal JS** – only if you add behaviour (e.g. smooth scroll to `#kontakt`, simple analytics).

---

## 3. Role of each file

| File | Purpose |
|------|--------|
| **index.html** | Structure and content only. `<link rel="stylesheet" href="styles.css">`, optional `<script src="script.js">`. No inline `<style>`. |
| **styles.css** | All visual styling. Can be grouped by: base, layout, components (hero, cards, CTAs, footer), utilities. |
| **script.js** | Optional. Start empty; add only for real behaviour (e.g. smooth scroll, form validation later). |
| **assets/** | Optional. Favicon, logo, or section images when you have them. |

---

## 4. Benefits

- **Maintainability:** CSS in one place; easier to tweak styles without scrolling through HTML.
- **Caching:** Browser can cache `styles.css` across page loads (relevant if you add more pages later).
- **Alignment with project-map:** Matches the described structure (index, styles, script, assets).
- **Clarity:** Clear separation: HTML = structure/content, CSS = presentation, JS = behaviour.
- **Future-ready:** Room for a contact form, analytics, or assets without restructuring later.

---

## 5. What we deliberately avoid

- **No bundler** (no Webpack, Vite, etc.) unless you explicitly want one.
- **No CSS/JS frameworks** – keep the stack minimal.
- **No extra pages yet** – single landing page is enough; add more only when needed.
- **No API or backend in this repo** – static site only; any future form/API can be handled via external service (e.g. Formspree, Supabase) and a small amount of JS.

---

## 6. Optional future extensions (out of scope for now)

- **Contact form:** Static form in HTML; submit via Formspree/Netlify Forms or similar; minimal JS for success/error message.
- **Analytics:** Add a single script tag (e.g. Plausible/Simple Analytics); no change to architecture.
- **Assets:** Drop favicon and images in `assets/` and reference from HTML/CSS.
- **Multiple pages:** Add e.g. `om.html`, `tjenester.html`; share `styles.css` and optional `script.js`.

---

## 7. Migration steps (when you decide to implement)

1. **Create `styles.css`** – Move all CSS from `<style>` in `index.html` into `styles.css`. Organize with short comments (e.g. `/* Base */`, `/* Hero */`, `/* CTAs */`).
2. **Update `index.html`** – Remove `<style>…</style>`. Add `<link rel="stylesheet" href="styles.css">` in `<head>`.
3. **Create `script.js`** – Empty file or minimal code (e.g. smooth scroll for `#kontakt`). Add `<script src="script.js"></script>` before `</body>` only if needed.
4. **Create `assets/`** – Empty folder or add `favicon.ico` (and reference it in `index.html`) when you have one.
5. **Test** – Open `index.html` locally and confirm layout and CTAs; then deploy to GitHub Pages and re-test.
6. **Update project-map** – No content change needed; structure will now match the described file layout.

---

## 8. Summary

- **Proposed change:** One logical step – move inline CSS to `styles.css`, keep HTML markup-only, add optional `script.js` and `assets/` so the repo matches the project-map and is easier to maintain and extend.
- **Scope:** Structure and file roles only; no design or copy changes.
- **Next:** Review this proposal; if you approve, the next step is to perform the migration (steps in §7) without changing behaviour or design.
