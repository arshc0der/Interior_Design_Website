# Issues Backlog (60 items)

This is the master list of known problems and ideas. Each item is meant to become a GitHub issue. Maintainers: copy an item into a new issue. Contributors: pick one, comment on the matching GitHub issue, then follow [CONTRIBUTING.md](../CONTRIBUTING.md).

> ✅ Item 55 (contribution docs, issue and PR templates) and part of 56 (`.editorconfig`, `.gitignore`) are already added. Check the [CHANGELOG](../CHANGELOG.md).

Reviewed: `index.html` (279 lines), `style.css` (390 lines), README, images/icons.
Key facts found: **0 `<script>` tags** (README claims JavaScript), **0 `@media` queries** (README claims responsive), **0 `alt` attributes**, **13 duplicated IDs**, only 1 HTML page, all links are `href="#"`.

Suggested labels: `bug`, `html`, `css`, `javascript`, `accessibility`, `seo`, `performance`, `documentation`, `enhancement`, `content`, `good first issue`, `help wanted`, `repo-setup`.
Difficulty: 🟢 easy (good first issue) · 🟡 medium · 🔴 hard

---

## 🐞 A. Bugs – HTML

### 1. Invalid closing tag `</section id="mid1">` 🟢
**Labels:** `bug`, `html`, `good first issue`
**File:** `index.html` line 44
A closing tag cannot have an attribute. Also, the opening `<section id="main">` has no matching `mid1` target anywhere.
**Tasks:** change to `</section>`; remove stray `#mid1` rule in CSS or use it properly.

### 2. Non-existent tag `<h1m>` used 5 times 🟢
**Labels:** `bug`, `html`, `good first issue`
**File:** `index.html` lines 47, 74, 143, 156, 176
`<h1m>` is not a valid HTML element, so these headings are not headings for browsers or screen readers.
**Tasks:** replace with `<h2>`; update CSS `#st-head` → class `.section-title`.

### 3. Duplicate IDs across the page (13 IDs repeated) 🟡
**Labels:** `bug`, `html`, `css`
`id="step1"`, `st-i`, `st-head`, `rate`, `price`, `recent`, `main-in`, `mh1`, `ab-gre`, `search`, `in-em`, `Send`, `main` are each used 2–6 times. IDs must be unique; this breaks `label for`, anchors, and any future JS.
**Tasks:** convert to classes (BEM naming), update CSS selectors accordingly.

### 4. Unclosed `<div id="recent">` in the blog section 🟢
**Labels:** `bug`, `html`, `good first issue`
**File:** `index.html` ~line 225
The blog `#recent` div is never closed before `</section>`. Browser auto-fixes it, but the markup is invalid.
**Tasks:** add the missing `</div>`; run the W3C validator and attach the clean result.

### 5. `id="main"` used for two different things 🟢
**Labels:** `bug`, `html`
`<section id="main">` (hero) and `<div id="main">` (services checklist, line 145) clash. Same for `#main-in`.
**Tasks:** rename the services block to `.service-list`.

### 6. Invalid list structure in navbar 🟡
**Labels:** `bug`, `html`, `accessibility`
**File:** lines 17–28
`<p>` and a nested `<ul>` are placed directly inside `<ul id="nav-ul">`. Only `<li>` is valid there.
**Tasks:** wrap in `<nav>`, put logo outside the `<ul>`, wrap nested list inside an `<li>` or flatten it.

### 7. Backslashes used in asset paths 🟢
**Labels:** `bug`, `html`, `good first issue`
**File:** `icons\question.png`, `images\1.jpg`, etc. (~25 places)
Backslashes work on Windows only; on GitHub Pages / Linux / Netlify the images break.
**Tasks:** replace all `\` with `/`; verify on a Linux/GitHub Pages deploy.

### 8. Broken HTML entity `&#169` (missing semicolon) 🟢
**Labels:** `bug`, `html`, `good first issue`
**File:** line 277 → should be `&#169;` or `&copy;`.

### 9. Wrong form semantics: email "form" is not a `<form>` 🟡
**Labels:** `bug`, `html`
**File:** lines 36–39, 232–235
`required` has no effect because inputs are not wrapped in `<form>`. The "Send us" button does nothing.
**Tasks:** wrap in `<form>`, add `name`, `autocomplete="email"`, `type="submit"` button, and a `<label>`.

### 10. CSS typo: `font-style: 18px` 🟢
**Labels:** `bug`, `css`, `good first issue`
**File:** `style.css` line 159 (`.head-st`). Should be `font-size: 18px`.

### 11. Dead / unused CSS selectors 🟢
**Labels:** `css`, `good first issue`
`#inflft`, `#mid1`, `#in1` conflicts, `.lft` duplicates, and unused `5.jpg` / `7.jpg` images in `/images`.
**Tasks:** remove unused rules and unused files (or use them in a gallery).

### 12. `#in-em::placeholder` has no effect for `margin`/`padding` 🟢
**Labels:** `bug`, `css`
**File:** `style.css` lines 121–125. Margin/padding are not applicable to `::placeholder`. Also missing newline before `/*mid*/`.

### 13. Hero search box overflows / input width hard-coded to 78% 🟡
**Labels:** `bug`, `css`
`#in-em{width:78%}` + `#Send{width:80px}` can overflow at certain widths. Use flexbox `flex:1`.

### 14. Hover on cards adds a border and shifts layout 🟢
**Labels:** `bug`, `css`
`.pro1:hover{border:2px solid grey}` and `.ex:hover{border:2px solid black}` make the element grow and "jump". Use `outline`, `box-shadow`, or reserve a transparent border by default.

### 15. Rating icon is the same size as a text glyph, with `height:10px` on a 512px PNG 🟢
**Labels:** `css`, `performance`
Large icons (512×512) are shown at 10–20px. Resize assets or switch to inline SVG.

---

## 📱 B. Responsive & Layout

### 16. No media queries – site is not responsive despite README claim 🔴
**Labels:** `bug`, `css`, `help wanted`
**File:** `style.css` has 0 `@media` rules. Hero (`.lft` padding 100px, `#mh1` 70px), 4-column navbar, and `.steps{width:30%}` all break on phones.
**Tasks:** add breakpoints (≥1024, 768, 480); stack hero columns; reduce paddings and font sizes. Test with Chrome DevTools.

### 17. Mobile navigation (hamburger menu) missing 🟡
**Labels:** `enhancement`, `javascript`, `css`
Navbar is a horizontal flex row and will overflow on small screens.
**Tasks:** add a toggle button with `aria-expanded`, animated slide-in menu, close on link click.

### 18. Fixed heights cause content clipping 🟡
**Labels:** `bug`, `css`
`#main-in{height:80vh}`, `.fo-part{height:200px}`, `.de-al{height:300px}` will clip or overlap text when content wraps.
**Tasks:** use `min-height`; test with zoom 200%.

### 19. Percent widths + margins push cards to wrap incorrectly 🟡
**Labels:** `bug`, `css`
`.pro1{width:24%;margin:10px}` + padding without `box-sizing:border-box`; 3 cards in a row leave awkward space and wrap to 2 on mid widths.
**Tasks:** add global `box-sizing:border-box`, replace flex-percentage layout with CSS Grid `repeat(auto-fit,minmax(260px,1fr))`.

### 20. Project card images use fixed `width:300px; height:200px` 🟢
**Labels:** `bug`, `css`
Images don't scale with the card and get stretched (aspect ratios vary 1280×720 to 1280×1012).
**Tasks:** `width:100%; aspect-ratio:3/2; object-fit:cover`.

### 21. "Infra Interiors" image `#inbg` fixed to height 500px, can overflow on mobile 🟢
**Labels:** `css`, `good first issue`
Use `max-width:100%; height:auto`.

### 22. Footer layout breaks on narrow screens 🟡
**Labels:** `css`, `bug`
Footer columns use `height:200px` and flex wrap; text can overlap the copyright line. Use grid with responsive columns.

### 23. Add CSS reset / base styles and a modern design-token system 🟡
**Labels:** `enhancement`, `css`
Replace `*{margin:0;padding:0}` with a proper reset; define CSS variables for colors (`#cae1ea`, `#f9d9be`, black), spacing, radii, font sizes.

---

## ♿ C. Accessibility

### 24. All images are missing `alt` text 🟢
**Labels:** `accessibility`, `html`, `good first issue`
0 of ~14 `<img>` have `alt`. Add meaningful alt for project photos and `alt=""` for decorative icons.

### 25. No semantic landmarks (`header`, `nav`, `main`, `footer`) 🟡
**Labels:** `accessibility`, `html`
Page is made of `div`/`section`/`p`. Add `<header>`, `<nav aria-label="Primary">`, `<main>`, `<footer>`, and a "Skip to content" link.

### 26. Heading hierarchy is wrong (multiple `<h1>`, `<p>` used as headings) 🟡
**Labels:** `accessibility`, `html`
`<h1>` appears in hero, "INFRA INTERIORS", newsletter. Use one `<h1>`, then `<h2>/<h3>`. Cards' titles (`.head-recent`) should be `<h3>`.

### 27. Color contrast failures 🟡
**Labels:** `accessibility`, `css`
Grey text (`#grey` on `#cae1ea → #f9d9be` gradient, `#st-i`, `#fo-dec`, `#dec-body`) is below 4.5:1 in places. Audit with Lighthouse/axe and fix.

### 28. `outline:none` on inputs removes focus indication 🟢
**Labels:** `accessibility`, `css`, `good first issue`
**File:** `style.css` line 389. Add a visible `:focus-visible` style for inputs, links, and buttons. Hover styles also need matching `:focus` styles.

### 29. Links with `href="#"` – no real destinations 🟢
**Labels:** `bug`, `accessibility`, `html`
Every nav, "Explore", "Read", "Read Policy", and footer item goes nowhere (scrolls to top). Footer items are `<br>`-separated text, not links.
**Tasks:** add section anchors (`#about`, `#projects`…) or separate pages; make footer items `<ul><li><a>`.

### 30. Email input has no `<label>` / accessible name 🟢
**Labels:** `accessibility`, `html`, `good first issue`
Placeholder is not a label. Add visually-hidden labels; add `aria-live` region for success/error messages.

### 31. Add `prefers-reduced-motion` and `prefers-color-scheme` support 🟡
**Labels:** `accessibility`, `css`, `enhancement`
Needed once animations are added; also enables a dark theme.

---

## 🔎 D. SEO & Meta

### 32. Missing meta description, Open Graph, Twitter cards, favicon 🟢
**Labels:** `seo`, `html`, `good first issue`
`<title>Interiors</title>` is the only metadata. Add description, `og:title/image/url`, `twitter:card`, favicon (`.ico` + `apple-touch-icon`), `theme-color`.

### 33. Improve `<title>`, add canonical URL, `robots.txt`, `sitemap.xml`, and JSON-LD (`LocalBusiness`/`Organization`) 🟡
**Labels:** `seo`, `enhancement`

---

## ⚡ E. Performance

### 34. Oversized images (≈3.4 MB in `/images`) 🟡
**Labels:** `performance`, `good first issue`
Images are 1280px+ JPEG/PNG (e.g. `2.jpg` 487 KB, `7.jpg` 419 KB) but displayed at 300×200. Provide WebP/AVIF versions and `srcset`/`sizes`.

### 35. No lazy loading, no width/height on images (layout shift) 🟢
**Labels:** `performance`, `html`, `good first issue`
Add `loading="lazy"`, `decoding="async"`, and explicit `width`/`height` to every `<img>` below the fold.

### 36. Oversized icons (512×512 PNGs shown at 10–20 px) and 35 KB `question.png` 🟢
**Labels:** `performance`
Replace with optimized SVG sprites.

### 37. Preview screenshots in repo (`preview/infra.png` 1140×4177) bloat the clone 🟢
**Labels:** `performance`, `documentation`
Compress / convert to WebP and reference relative path in README.

### 38. Use a real web font instead of `font-family: fantasy` / default serif 🟡
**Labels:** `css`, `enhancement`, `performance`
`fantasy` renders very differently per OS. Add a self-hosted font (e.g. Poppins/Playfair) with `font-display:swap` and a fallback stack; body currently has no `font-family`.

---

## ✨ F. Features / Enhancements

### 39. Add JavaScript: README says JS is used, but there is none 🔴
**Labels:** `enhancement`, `javascript`, `help wanted`
Add `script.js` for the mobile menu, smooth scroll, form validation, and scroll-reveal animations. Alternatively correct the README (see issue 53).

### 40. Working newsletter / contact form with validation 🟡
**Labels:** `enhancement`, `javascript`
Client-side validation, success/error messages, and integration with Formspree/Netlify Forms/EmailJS. Hero form and newsletter form should use different actions.

### 41. Project gallery with filter and lightbox 🔴
**Labels:** `enhancement`, `javascript`, `help wanted`
Filter by room (Living, Bedroom, Kitchen…); lightbox with keyboard navigation. Use the unused `5.jpg` and `7.jpg`.

### 42. Before/after image slider component 🔴
**Labels:** `enhancement`, `javascript`, `help wanted`
Core feature for interior designers.

### 43. Add pages: About, Projects, Services, Contact, Blog post template, 404 🔴
**Labels:** `enhancement`, `html`, `help wanted`
Navbar lists About/Projects/Agents/Services/Listings but none exist.

### 44. Testimonials / client reviews section and a "Book a consultation" CTA 🟡
**Labels:** `enhancement`, `content`

### 45. Dark mode toggle with saved preference 🟡
**Labels:** `enhancement`, `css`, `javascript`

### 46. Scroll animations, sticky navbar and "back to top" button 🟡
**Labels:** `enhancement`, `css`, `javascript`

### 47. Embed Google Map / office locations in "Where are we?" 🟡
**Labels:** `enhancement`
Section claims "50+ Branch, 21+ Main Office" but shows only a background image.

### 48. Multi-language (i18n) support 🔴
**Labels:** `enhancement`, `help wanted`

---

## 📝 G. Content & Copy (many are good first issues)

### 49. Fix spelling and grammar mistakes across the site 🟢
**Labels:** `content`, `good first issue`
Examples: `ifra` → `infra`, `hassite` → `hassle`, `youe` → `your`, `comapny` → `company`, `Resouces` → `Resources`, `Blod` → `Blog`, `Ofiice` → `Office`, `Rigths` → `Rights`, `enviornment` → `environment`, `plaese` → `please`, "take this completed the project with in time and fund by customer".

### 50. Copy is leftover from an **insurance** template 🟢
**Labels:** `content`, `bug`, `good first issue`
"Getting insured is as easy…", "Easy to manage policy", "File claim in 3 minutes", "Our Policy", "save 20%". Rewrite for interior design (consultation, mood board, quote, execution).

### 51. All cards are identical placeholder content (3 projects + 3 blog posts) 🟢
**Labels:** `content`, `good first issue`
Same title "Modern Design Interior", rating 4.3, price $500, and text repeated 6 times. Blog cards show rating and price, which make no sense for articles. Create distinct blog cards (title, date, author, read time).

### 52. Make content data-driven (JSON) instead of copy-pasted HTML 🔴
**Labels:** `enhancement`, `javascript`, `help wanted`
Move projects/blog posts into `data/projects.json` and render with JS templates to avoid duplicated markup.

---

## 📚 H. Documentation & Repo Setup

### 53. README claims don't match the code 🟢
**Labels:** `documentation`, `good first issue`
README advertises JavaScript, responsiveness, interactive galleries, cross-browser testing. Update to reflect reality or implement the features. Also "Platform: Windows" badge is incorrect for a static site.

### 54. LICENSE link in README points to opensource.org instead of the local file 🟢
**Labels:** `documentation`, `good first issue`
Use ``[LICENSE](LICENSE)``. Also add the live demo link (GitHub Pages).

### 55. Add `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, issue and PR templates 🟢
**Labels:** `repo-setup`, `documentation`, `good first issue`

### 56. Add `.gitignore`, `.editorconfig`, Prettier/Stylelint/HTMLHint configs 🟡
**Labels:** `repo-setup`

### 57. Add GitHub Actions CI (HTML validation, link check, Lighthouse CI) 🟡
**Labels:** `repo-setup`, `help wanted`

### 58. Deploy to GitHub Pages and add a live demo badge 🟢
**Labels:** `repo-setup`, `good first issue`

### 59. Add a `CHANGELOG.md` and semantic version tags 🟢
**Labels:** `documentation`, `repo-setup`

### 60. Restructure project folders (`assets/css`, `assets/js`, `assets/img`) and rename files (`inra.png` → `logo.png`, `bg.4.jpg` → `newsletter-bg.jpg`) 🟡
**Labels:** `repo-setup`, `good first issue`
Current names are inconsistent (`bg.4.jpg`, `inra.png` typo) and use the dot in the filename.

---

## Suggested "good first issue" set
1, 2, 4, 7, 8, 10, 11, 12, 21, 24, 28, 30, 32, 35, 36, 49, 50, 51, 53, 54, 55, 58, 60
