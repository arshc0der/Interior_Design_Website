# Project Structure

A quick map of the project so you know where to look before changing something.

## Files and folders

| Path | Purpose |
| --- | --- |
| `index.html` | The entire website. All sections live in this one file. |
| `style.css` | All CSS. Linked from `index.html` with `<link rel="stylesheet" href="style.css">`. |
| `images/` | Photos (`1.jpg`–`8.jpg`) and backgrounds (`bg*.jpg`, `inra.png`). |
| `icons/` | Small PNG icons used in steps, ratings and checklists. |
| `preview/` | Screenshots used in the README. Not used by the website. |
| `docs/` | Guides for contributors. |
| `.github/` | Issue templates, pull request template, code owners. |

## Sections of the page (top to bottom)

| # | Section | HTML `id` | What it shows |
| --- | --- | --- | --- |
| 1 | Hero | `#main` | Navigation bar, headline, email box, background image |
| 2 | Steps | `#step1`, `#step34` | "Three steps, three minutes" with three icons |
| 3 | Recent projects | `#recentpro` | Three project cards (image, rating, price, button) |
| 4 | Brand banner | `#infra` | Large "INFRA INTERIORS" text and logo image |
| 5 | Services | `#que-betet` | Image plus a checklist of benefits |
| 6 | Locations | `#locate` | Company policy text, numbers (branches, projects, offices) |
| 7 | Blog | `#blog` | Three blog preview cards |
| 8 | Newsletter | `#letter` | Email signup box and image |
| 9 | Footer | `#footer`, `#ffoot` | Link columns and copyright |

## How CSS is organized

`style.css` follows the page from top to bottom. Each part has a comment such as `/*recent project start here*/`. To find the style for an element, copy its `id` or `class` from `index.html` and search for it in `style.css`.

> ⚠️ Some `id` names are used more than once on the page, which is a known issue (see the [backlog](ISSUES_BACKLOG.md), item 3). If you change a style, check that it does not affect other sections by accident.

## Where to start for common tasks

| I want to... | Open |
| --- | --- |
| Change text | `index.html` |
| Change a color | `style.css` (search for the color code) |
| Replace a photo | `images/` and the matching `<img>` or `url()` |
| Fix the layout on phones | `style.css` (add `@media` rules at the bottom) |
| Improve the docs | `README.md` or `docs/` |
