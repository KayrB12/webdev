Project overview

- This repository is a small static-HTML exercise site (no build system). The main content is under the "Day 1" folder and contains multiple simple pages and image assets used for learning HTML/CSS.

Key locations (examples)

- Resume pages: [Day 1/resume/index.html](Day%201/resume/index.html)
- Color-design example: [Day 1/resume/color-design/index.html](Day%201/resume/color-design/index.html)
- Common assets folder: [Day 1/resume/images](Day%201/resume/images)

Big-picture notes for an agent

- Static site only: there is no `package.json`, build pipeline, or test runner. Changes are limited to editing `.html`, image files, and in-page CSS.
- Folder names contain spaces (e.g., "HTML skeleton" and "Day 1"). Preserve those names — do not rename folders unless the user requests it.
- Windows is the current dev OS; filename case inconsistencies exist (e.g., `Images/grad2.jpg` vs `images/grad2.jpg` in [Day 1/resume/index.html](Day%201/resume/index.html)). On Windows these both work, but avoid changing case if the site may be moved to a case-sensitive host.

Project-specific patterns and conventions

- Styles are primarily inline or inside a `<style>` block in each HTML file (see `color-design/index.html`). When adding styles, follow the existing pattern: small scoped `<style>` blocks near the top of each page.
- Lightweight class/ID usage examples found in `color-design/index.html`:
  - `.highlight` — short, padded background blocks
  - `.list-container` — grouped lists with rounded background
  - `#color-explanation` — single-page section with distinctive styling
- Images are referenced with relative paths from the HTML file. Typical usage:
  - `<img src="Images/grad2.jpg">` in `Day 1/resume/index.html`
  - Keep relative linking; when moving files, update links to use `../` where appropriate.

Developer workflows (what actually works here)

- Quick preview in the editor: open the file in a browser or use VS Code Live Server.
- Quick local HTTP server (recommended if testing relative paths):

```powershell
# from the repository root
python -m http.server 8000
# then open http://localhost:8000/Day%201/resume/index.html
```

- No CI or tests to run. Use manual review and browser testing for verification.

What agents should do (practical, actionable rules)

- Do not introduce new build tooling or dependencies unless the user requests it explicitly.
- Preserve folder names and relative links; if you must rename or move a file, update all relative links in the same commit and call out the change in the PR description.
- When fixing HTML or CSS, keep edits minimal and fix only the root cause (e.g., close unclosed tags, correct mismatched `Images` vs `images` references). Example actionable fixes found:
  - Close unclosed `<h3>` tags in `Day 1/resume/index.html`.
  - Standardize image paths to the existing `Day 1/resume/images` folder and keep casing consistent.
- Prefer small, self-contained changes per PR (one page or one set of linked files). Run a browser preview after edits.

When to ask the user

- Ask before renaming folders, changing the top-level structure, or adding new tooling (linters, bundlers, servers).
- Ask before deleting images or other media assets.

If you need more context

- Inspect the two representative pages above to see common code style and HTML patterns. If you want, I can run a quick pass to fix small HTML issues (unclosed tags, inconsistent image paths) and then open the preview.
