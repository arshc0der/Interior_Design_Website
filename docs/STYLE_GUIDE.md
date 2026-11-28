# Style Guide

Simple rules that keep the code easy to read. If you are unsure, copy the style of nearby code.

## General

- Use **4 spaces** for indentation (no tabs). The `.editorconfig` file sets this up in most editors.
- Use **UTF-8** and **LF** line endings.
- End every file with a new line.
- Keep changes small and focused on one issue.

## HTML

- Use lowercase tags and attributes.
- Always close tags and use double quotes: `<img src="images/1.jpg" alt="Modern living room">`.
- Use **forward slashes** in paths: `images/1.jpg`, never `images\1.jpg`.
- Add an `alt` attribute to every image. Use `alt=""` for purely decorative images.
- Every `id` must be **unique**. Prefer **classes** for repeated elements.
- Use meaningful tags: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`, `<h1>`–`<h6>`, `<button>`.
- Only one `<h1>` per page, and do not skip heading levels.
- Links that open a new tab need `rel="noopener noreferrer"`.

## CSS

- One rule per selector, one declaration per line.
- Prefer classes over ids for styling.
- Use lowercase class names with hyphens: `.project-card`, `.nav-link`.
- Do not use `!important` unless there is no other way.
- Do not remove focus outlines without giving a replacement style (`:focus-visible`).
- Add responsive rules with `@media` at the end of the file, mobile-friendly sizes first when possible.
- Group related rules and label them with a comment, like the existing sections.
- Reuse the project's colors: `#cae1ea`, `#f9d9be`, black and white.

## Images

- Keep images under about 200 KB when possible. Use WebP or compressed JPEG.
- Use lowercase file names with hyphens: `living-room.jpg`.
- Only add images you have the right to use. Name the source in your pull request.

## JavaScript (when added)

- Put code in a separate `script.js` file loaded with `defer`.
- Use `const` and `let`, never `var`.
- Use clear names and short comments for tricky parts.

## Commit messages

Format: `type: short description (#issue)`

| Type | Use for |
| --- | --- |
| `fix` | A bug fix |
| `feat` | A new feature |
| `docs` | Documentation only |
| `style` | Formatting, no logic change |
| `refactor` | Code cleanup without changing the result |
| `perf` | Speed or image-size improvements |
| `chore` | Tooling and project files |

Examples:

```text
fix: replace backslashes in image paths (#7)
docs: add setup steps for Windows (#55)
feat: add mobile navigation menu (#17)
```

## Branch names

`type/short-description`, for example `fix/image-paths`, `docs/readme-update`, `feature/mobile-menu`.

## Pull request checklist

- [ ] Works in Chrome and Firefox
- [ ] Looks right on a narrow window
- [ ] No unrelated changes
- [ ] Linked the issue (`Closes #number`)
