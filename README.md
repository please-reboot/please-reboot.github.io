# Resume, as code

My resume lives here as data (`resume.json`, following the [JSON Resume](https://jsonresume.org/) schema), not as a Word doc. Every push to `main` triggers a GitHub Action that renders it to a themed HTML page and a PDF, then publishes both to GitHub Pages.

**Live site:** https://please-reboot.github.io/

## How it works

- `resume.json` — the single source of truth. Edit this file to update the resume.
- `.github/workflows/build.yml` — on every push to `master`, validates the JSON, renders it with [`resumed`](https://github.com/rbardini/resumed) using the `jsonresume-theme-even` theme, packages the output (`index.html` and the raw `resume.json`) as a Pages artifact, and deploys it. (PDF export is left out of CI — GitHub's runner sandbox blocks the headless Chrome Puppeteer needs; run `resumed export resume.json --theme jsonresume-theme-even --output resume.pdf` locally if you want a PDF.)
- In repo Settings → Pages, the **Source** must be set to **GitHub Actions** (not "Deploy from a branch") for this workflow to publish the site.

## Updating the resume

1. Edit `resume.json` (add a job under `work`, tweak `highlights`, update `skills`, etc.) — see the [JSON Resume schema](https://jsonresume.org/schema/) for the full field list.
2. Commit and push to `master`.
3. The Action rebuilds and republishes automatically within a minute or two.

## Trying a different look

Swap `jsonresume-theme-even` for any other [JSON Resume theme](https://jsonresume.org/themes/) (e.g. `jsonresume-theme-stackoverflow`, `jsonresume-theme-kendall`) in `build.yml` — no other changes needed.
