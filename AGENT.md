AGENT.md
This document describes how to analyze, improve, and maintain the Visual Analytics Demo project using automated agents and manual contributors. It outlines the current state, goals, recommended architecture, and a practical task plan.

Overview
- Project: A small static web dashboard visualizing IMDb data using D3, Crossfilter, and DC.js.
- Key files: `index.html`, `js/d3.js`, `js/crossfilter.js`, `js/dc.js`, `css/*`, and data files like `movies_imdb.csv` and `movie_metadata_orig.csv`.
- Running: Open `index.html` in a browser or serve the repo with a static server.

Current Observations (as of this repo state)
- All visualization logic is embedded in a large inline script inside `index.html` with a single `createGraph` function and a lot of DOM wiring.
- No package.json or dev tooling is present; no automated tests or linting.
- Data loading and transformation are done directly in the UI code, which makes testing harder and reuse of data logic limited.
- Accessibility and responsive considerations are minimal (checkboxes and charts exist but ARIA labeling and responsive tweaks are limited).

Mission for AGENTS
- Improve maintainability, testability, performance, and accessibility without breaking visuals.
- Introduce lightweight tooling to enable quick dev cycles (serving, linting, minimal tests).
- Create a small, well-documented code structure that isolates data loading, data transformations, and visual components.
- Provide an actionable backlog with clear acceptance criteria.

Proposed Architecture Improvements
- Split concerns:
  - data.js: data loading and preprocessing (CSV loading, parsing, validation)
  - charting.js: DC.js chart setup and rendering logic
  - ui.js: controls and event handling (genre checkboxes, year slider, reset)
  - config.js: constants (data paths, color schemes, chart options)
- Use modules (ESM) or lightweight namespaces to avoid polluting global scope.
- Add a small state machine or centralized store for UI state (selected genres, year range).
- Add error handling and loading indicators for CSV fetches.

Code Quality and Tooling
- Add ESLint with a sensible config and migrate old code patterns where feasible.
- Add a basic pre-commit hook or CI step to run linting on changes.
- Add a minimal npm-based dev server (e.g., `http-server` or `vite`) and a script like `npm run serve`.
- Add a basic test scaffold (e.g., Jest) for pure data-processing helpers if any are introduced.

Accessibility and UX
- Add ARIA attributes to controls; ensure keyboard navigability.
- Improve color contrast and provide a high-contrast theme toggle if needed in the future.
- Make the layout more responsive for mobile viewports.

Data Quality and Provenance
- Document source datasets, with last-updated timestamps and license notes.
- Add a simple data validation pass for CSV columns used by charts.

Minimal Backlog (example tasks)
- [ ] Add package.json and a dev server script; add npm run serve.
- [ ] Create modular JS files: data.js, charting.js, ui.js, config.js; refactor index.html to load modules.
- [ ] Introduce ESLint config and run lint; fix obvious issues.
- [ ] Add ARIA labels to genre checkboxes and sliders; ensure focus styles are visible.
- [ ] Add basic data validation for `movie_metadata_orig.csv` and `movies_imdb.csv`.
- [ ] Write a tiny unit test for a data parsing helper (if extracted).
- [ ] Add README.md with quick-start and architecture notes.

Acceptance Criteria per Task
- Code is modular and easier to maintain; charts still render correctly after refactor.
- Lint passes; no obvious global variable leaks.
- Dev server runs with minimal commands; repo has a README with setup steps.
- Accessibility cues improved and keyboard accessible controls exist.

How to Use This AGENT.md
- Use as a blueprint for future PRs and automation tasks.
- When starting a new improvement sprint, draft a task list based on the backlog above and attach it to a PR description or a project board.

Appendix: References in this Repo
- HTML entry: `index.html` (dashboard shell)
- Data: `movies_imdb.csv`, `movie_metadata_orig.csv`
- JS libs: `js/d3.js`, `js/crossfilter.js`, `js/dc.js` (and other supporting scripts)
- Styles: `css/*.css` and theme classes in the HTML

If you want me to implement any of these steps, say which tasks to tackle and I will propose concrete changes and patches.
