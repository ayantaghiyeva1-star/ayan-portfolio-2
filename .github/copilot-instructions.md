<!-- Copilot / AI helper instructions for this repository -->
# Project overview

This repository is a small, static personal portfolio site built with plain HTML, CSS and JavaScript.
There is no build tool or package manager: the site runs by opening `index.html` or serving the folder as static files.

# Key files

- `index.html` — the single-page structure and content. Sections use `id` attributes (e.g. `#home`, `#about`, `#projects`).
- `styles.css` — global styling; color tokens live in `:root` CSS variables and should be edited there.
- `script.js` — client-side behavior: mobile menu toggling, smooth scrolling, IntersectionObserver animations, and a placeholder contact form handler.
- `README.md` — developer notes and quick start (no build required).

# Big picture & design decisions

- Intention: minimal, framework-free portfolio for quick edits and static hosting.
- JavaScript manipulates DOM directly (no frameworks). Follow existing class and id names when modifying markup so `script.js` selectors keep working.
- Contact form is a front-end placeholder — it displays an alert and resets the form. Backend integration must replace the submit handler in `script.js`.

# Project-specific conventions (copy/paste friendly)

- Navigation links target section IDs: keep `href="#section-id"` and `class="nav-link"` so smooth scroll and active-state logic continue to work.
- Mobile menu uses `.hamburger` and `.nav-menu` classes. Toggle these classes to open/close the mobile menu.
- Animations rely on selecting items with `.project-card`, `.skill-category`, or `.stat-item`. Preserve these classes when adding elements to be observed.
- Stat counters are numeric text inside elements with `.stat-number`. The JS parses digits with `parseInt()`; keep the number visible in the text.

# Common edit tasks — examples

- Change site owner name (hero): edit the `.name` span in `index.html`.
- Add a project: copy an existing `.project-card` in `index.html` and update `.project-title`, `.project-description`, `.project-tech` and `.project-links`.
- Wire contact form to a backend: replace the `contactForm.addEventListener('submit', ...)` block in `script.js` with `fetch()` or `XMLHttpRequest` logic; ensure element IDs `name`, `email`, `message` and `contactForm` remain the same.

# Development & debugging workflows

- Run locally (static server):
  - Python 3: `python3 -m http.server 8000` then open `http://localhost:8000`.
  - Or use VS Code Live Server extension.
- Debugging: use browser DevTools console. Common issues are missing DOM nodes (e.g., `contactForm` may be absent if contact section is removed). Guard code accordingly.

# What AI agents should preserve

- Do not introduce a build system or new frameworks unless the task explicitly requires it.
- Preserve class and id names unless you update the corresponding selectors in `script.js` and `styles.css`.
- Keep changes minimal and focused: this project is intentionally small and static.

# Helpful snippets (copy into PRs)

- Add new project-card (replace content as needed):
```
<div class="project-card">...</div>
```

- Toggle mobile menu in JS (example uses existing classes):
```
document.querySelector('.hamburger').classList.toggle('active');
document.querySelector('.nav-menu').classList.toggle('active');
```

# Notes for reviewers

- Point out any selector/class renames so the agent can update `script.js` and `styles.css` consistently.
- If adding features that require state or routing, prefer keeping them optional and minimal to preserve the static site nature.

If anything here is unclear or you'd like the file to include additional examples (CSS variables, more JS snippets, or PR checklist items), tell me what to add.
