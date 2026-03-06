# Repository analysis and improvement suggestions

Analysis of the **berntsenstruktur** repo with concrete, prioritised improvement suggestions. Explain changes in Norwegian; code in English.

---

## 1. Current state summary

| Area | Status |
|------|--------|
| **Entry** | Single `index.html` (~260 lines, HTML + inline CSS) |
| **CSS** | Inline in `<style>`; no `styles.css` |
| **JS** | None; no `script.js` |
| **Assets** | None; no `assets/` or favicon |
| **Docs** | README nearly empty; ARCHITECTURE.md describes target structure |
| **Config** | CNAME (berntsenstruktur.no), .gitattributes (LF) |
| **Cursor** | project-map, project, language, webdev, openai-only, migrate-to-skills command |

**Alignment with project-map:** Landing sections (Hero → Services → Process → Who → Contact) are correct. File structure (styles.css, script.js, assets/) is **not** implemented yet.

---

## 2. Suggested improvements (prioritised)

### High priority

#### 2.1 Implement ARCHITECTURE.md (file structure)
- **What:** Create `styles.css`, move all CSS from `index.html` into it; add `<link rel="stylesheet" href="styles.css">`. Optionally add empty `script.js` and `assets/` (or `assets/.gitkeep`).
- **Why:** Matches project-map, improves maintainability and caching; ARCHITECTURE.md already describes the steps.
- **Effort:** Low (copy/paste CSS, one link tag).

#### 2.2 Add favicon
- **What:** Add `assets/favicon.ico` (or SVG) and in `index.html`: `<link rel="icon" href="assets/favicon.ico" type="image/x-icon">`.
- **Why:** Avoids 404 on `/favicon.ico`, better branding in tabs and bookmarks.
- **Effort:** Low (once you have a favicon asset).

#### 2.3 Expand README.md
- **What:** Short description: purpose (berntsenstruktur.no landing page), tech (HTML/CSS/JS, GitHub Pages), how to run locally (open `index.html` or use a simple server), and link to ARCHITECTURE.md.
- **Why:** Helps you and others understand the repo at a glance; good practice for GitHub.
- **Effort:** Low.

#### 2.4 Remove or repurpose empty file
- **What:** `.cursor/rules/Nytt Tekstdokument.txt` is empty. Delete it or replace with real content.
- **Why:** Reduces noise and avoids confusion.
- **Effort:** Trivial.

---

### Medium priority

#### 2.5 Preconnect for Google Fonts
- **What:** In `<head>`, before the font link, add:
  ```html
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  ```
- **Why:** Can improve font load time (DNS/TLS earlier).
- **Effort:** Low.

#### 2.6 Custom 404 for GitHub Pages
- **What:** Add `404.html` in the repo root with the same look as the site (reuse styles) and a message + link back to the front page.
- **Why:** Better UX when someone hits a missing URL on berntsenstruktur.no.
- **Effort:** Low–medium (one extra HTML page).

#### 2.7 Optional: skip link for accessibility
- **What:** First focusable element: `<a href="#hero" class="skip-link">Hopp til innhold</a>`, styled to be visible on focus only (e.g. position absolute, show on :focus).
- **Why:** Improves keyboard and screen-reader navigation.
- **Effort:** Low.

#### 2.8 Optional: contact form
- **What:** Replace or complement mailto with a simple form; submit via Formspree/Netlify Forms (or similar); minimal JS for success/error.
- **Why:** Some users prefer forms to opening an email client.
- **Effort:** Medium (form HTML, optional script, external service config).

---

### Lower priority / later

#### 2.9 Analytics (privacy-friendly)
- **What:** If you want traffic insight, add a single script from e.g. Plausible or Simple Analytics (no cookies, GDPR-friendly).
- **Why:** Understand visits without changing architecture.
- **Effort:** Low once account is set up.

#### 2.10 Open Graph / Twitter meta tags
- **What:** Add `og:title`, `og:description`, `og:url`, `og:type`, and optionally `twitter:card` so shares look good on social.
- **Why:** Better preview when the site is shared.
- **Effort:** Low (a few meta tags).

#### 2.11 Consolidate Cursor rules
- **What:** project-map.md, project.md, language.md, and webdev.md overlap. Consider keeping one source of truth (e.g. project-map) and having others reference it or merge content.
- **Why:** Less duplication, easier to maintain.
- **Effort:** Low–medium.

---

## 3. What to avoid (per project rules)

- No build step, no frameworks, no unnecessary dependencies.
- No backend/API in this repo; keep it static (GitHub Pages).
- Do not add `styles.css`/`script.js` in a way that requires a build (e.g. keep plain CSS/JS).

---

## 4. Quick wins checklist

- [ ] Move CSS to `styles.css` and link it from `index.html`.
- [ ] Add README with purpose, tech, and local run instructions.
- [ ] Delete or fill `.cursor/rules/Nytt Tekstdokument.txt`.
- [ ] Add `rel="preconnect"` for Google Fonts.
- [ ] Add favicon when you have the asset; reference from `index.html`.
- [ ] (Optional) Add `404.html` and skip-link.

---

## 5. Summary

The site and repo are in good shape: clear sections, semantic HTML, CTAs, and a11y (focus, reduced motion) already improved. The main gaps are **file structure** (CSS/JS/assets as in project-map), **documentation** (README), **favicon**, and small **performance/a11y** tweaks. Implementing §2.1–2.4 gives the largest benefit for little effort.
