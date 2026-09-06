# GitHub Pages deployment and updates

The dashboard is live at [the CECREH site](https://CECREH-2023.github.io/HUD-CDBG-DR-Fund-Hierarchy-Dashboard/). This repository publishes branch `main` from **/(root)** through GitHub Pages.

## Update the site

Build and validate changes in a local checkout. Commit application assets, data chunks, the narrative manifest, and documentation as one consistent version. Review removed files explicitly rather than deleting whole folders as an upload step. Preserve `index.html` and `.nojekyll` at the publishing root.

```bash
python scripts/validate_static_package.py --site-dir .
```

After pushing, confirm the Pages build in **Actions** and open the live page. Test filters, maps, narrative loading, and reports. The [README](README.md) documents rebuilding from separately prepared inputs.

## Deploy a fork

In the fork's **Settings → Pages**, choose **Deploy from a branch**, the intended branch, and **/(root)**. The branch must contain the full static application and its matching `assets/`, `data/`, and `privacy/` files. GitHub provides the fork's own URL after deployment.

## Public data boundary

Only screened public excerpts and aggregate privacy statistics belong in the public tree. Original narratives, detected-address QA records, and other unsanitized working inputs remain in the authorized source environment. The [privacy method](privacy/NARRATIVE_PRIVACY_METHOD.md) describes the handling rules and their limitations.

## Troubleshooting

- For a 404, check the publishing branch/root and Pages build status.
- For a blank or partly loaded page, check browser errors and whether application assets and data chunks came from the same build.
- Use a local HTTP server for the multi-file edition; the standalone compatibility HTML can be opened directly.
- If WebGL is unavailable, map views show a fallback message while other available controls continue to operate.
