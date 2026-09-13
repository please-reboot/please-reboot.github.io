# Resume, as code

My resume lives here as data (`resume.json`, following the [JSON Resume](https://jsonresume.org/) schema), not as a Word doc. Every push to `main` triggers a GitHub Action that renders it to a themed HTML page and a PDF, then publishes both to GitHub Pages.

**Live site:** https://please-reboot.github.io/

## How it works

- `resume.json` — the single source of truth. Edit this file to update the resume.
- `.github/workflows/build.yml` — on every push to `main`, validates the JSON, renders it with [`resumed`](https://github.com/rbardini/resumed) using the `jsonresume-theme-elegant` theme, and publishes the output (`index.html`, a downloadable PDF, and the raw `resume.json`) to the `gh-pages` branch.
- GitHub Pages is configured to serve from the `gh-pages` branch, so the rendered site goes live automatically after each push — no manual build step.

## Updating the resume

1. Edit `resume.json` (add a job under `work`, tweak `highlights`, update `skills`, etc.) — see the [JSON Resume schema](https://jsonresume.org/schema/) for the full field list.
2. Commit and push to `main`.
3. The Action rebuilds and republishes automatically within a minute or two.

## Trying a different look

Swap `jsonresume-theme-elegant` for any other [JSON Resume theme](https://jsonresume.org/themes/) (e.g. `jsonresume-theme-stackoverflow`, `jsonresume-theme-kendall`) in `build.yml` — no other changes needed.
