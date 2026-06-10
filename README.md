# robusta-docs

Public documentation site for **ROBUSTA** — the multi-tenant CRM + ERP platform.

**Live site:** [elytz.github.io/robusta-docs](https://elytz.github.io/robusta-docs)

This repo holds only the user-guide markdown plus the MkDocs Material build pipeline. The application source lives in a private repo; the docs are synced here so customers and integrators can read them without a license.

## Repo layout

```
mkdocs.yml                 — site config (nav, theme, plugins)
requirements.txt           — pip deps (mkdocs-material + mermaid)
.github/workflows/         — GitHub Action that builds + deploys on push
docs/
├── index.md               — landing page (the README from the source repo)
├── framework.md           — Framework & Setup screens
├── items.md, inventory.md, procurement.md, ...    — 17 section files
└── deep-dives/            — 6 deep-dive walkthroughs (currently TODO stubs)
```

## How updates land here

Docs are authored in the private source repo. On every push to that repo's `main` branch, an automated sync pushes the `docs/erp-guide/` contents to this repo's `main`, which then triggers the GitHub Pages build.

Drift between the source and this mirror should be zero. If you find an outdated page, open an issue and we'll trace the sync.

## Building locally

```bash
pip install -r requirements.txt
mkdocs serve     # local preview at http://127.0.0.1:8000
mkdocs build     # produces ./site
```

## License

Documentation is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The ROBUSTA application source itself is proprietary.
