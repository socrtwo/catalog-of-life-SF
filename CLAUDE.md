# CLAUDE.md

Converts the Catalogue of Life taxonomic database (~1.2M species) into
GEDCOM genealogy format so the tree of life can be rendered by any
genealogy tool. Ships as per-platform ZIPs that bundle the Access `.mdb`,
CSV/JSON exports, and a static HTML viewer.

## Repo map

- `Catalogue-of-Life-Converter-1.0.mdb` — the source Access database with
  the VBA / GEDCOM export macro. Windows-canonical.
- `data/` — CSV / JSON exports derived from the `.mdb` for non-Windows
  platforms (where Access isn't available).
- `web/` — the static HTML viewer that runs offline from `file://`.
  Powers the Web release ZIP and the GitHub Pages live page.
- `docs/platforms/` — per-platform install notes (Windows / macOS / Linux
  / ChromeOS / Android / iOS / Web).
- `INSTRUCTIONS.txt`, `Catalogue-of-Life-Connection.png` — legacy docs
  preserved from the SourceForge import.
- `.github/workflows/` — `pages.yml` (deploy `web/` to Pages on push to
  `main`), `release.yml` (build per-platform ZIPs on `v*` tag).

## Branch policy

Work on the assigned feature branch:

1. Commit and push the feature branch.
2. **Open a PR from the feature branch to `main`** using the GitHub MCP
   tools (`mcp__github__create_pull_request`). Do not merge directly —
   the maintainer reviews and merges.
3. Both the Pages live page and the GitHub Release pipeline fire from
   `main`, so nothing ships until the PR lands.

## Releasing

- Push a `v*` tag to `main` (or use Actions → Release → workflow_dispatch)
  to produce platform ZIPs: `catalog-of-life-{windows,macos,linux,chromeos,android,ios,web}.zip`.
- Every ZIP contains the appropriate subset of `data/`, the relevant
  docs from `docs/platforms/`, and (where applicable) the HTML viewer.

## Verifying changes

- Web viewer: open `web/index.html` directly in a browser (it must work
  from `file://` — that's a deliberate property of the Web release).
- Data export: if you regenerate CSVs from the `.mdb`, spot-check row
  counts and a few known species (e.g. `Homo sapiens`) before pushing.
- The `.mdb` itself is binary — Access changes can't be diffed
  meaningfully. Note what you changed in the commit message.

## Gotchas

- Only Windows + Access runs the VBA / GEDCOM export end-to-end. Other
  platforms get the pre-baked data exports. If you change the export
  logic in the `.mdb`, regenerate `data/` and commit both.
- The Web bundle must remain `file://`-runnable. Don't add code that
  needs `fetch()` against same-origin paths or modules served over HTTP.
- The dataset is ~1.2M rows. Avoid pulling everything into memory in the
  viewer — pagination / virtual scroll is load-bearing.
