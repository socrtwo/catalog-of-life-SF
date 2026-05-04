<!--MODERNIZED:v2-->
# Catalog of Life

> Converts the **Catalogue of Life** taxonomic database (~1.2 million species)
> into **GEDCOM** genealogy format, producing ~2 million records that can be
> rendered as a tree-of-life by any genealogy tool.

[![Live page](https://img.shields.io/badge/live-page-ff2e93?style=for-the-badge)](https://socrtwo.github.io/catalog-of-life-SF/)
[![Releases](https://img.shields.io/github/v/release/socrtwo/catalog-of-life-SF?style=for-the-badge&color=7c3aed)](https://github.com/socrtwo/catalog-of-life-SF/releases)
[![License](https://img.shields.io/github/license/socrtwo/catalog-of-life-SF?style=for-the-badge&color=22d3ee)](https://github.com/socrtwo/catalog-of-life-SF/blob/main/LICENSE)
[![Last commit](https://img.shields.io/github/last-commit/socrtwo/catalog-of-life-SF?style=for-the-badge&color=34d399)](https://github.com/socrtwo/catalog-of-life-SF/commits)

🌐 **Live:** <https://socrtwo.github.io/catalog-of-life-SF/>
📦 **Downloads:** [Releases](https://github.com/socrtwo/catalog-of-life-SF/releases)
📂 **Source:** [socrtwo/catalog-of-life-SF](https://github.com/socrtwo/catalog-of-life-SF)

---

## Downloads

Pick the bundle for your platform — every release ships a self-contained ZIP
with the database, platform-specific install notes, CSV / JSON data exports,
and (where applicable) a built-in HTML viewer.

| Platform | Asset | Best for |
|---|---|---|
| 🪟 **Windows**  | `catalog-of-life-windows.zip`  | Microsoft Access — full VBA / GEDCOM export |
| 🍎 **macOS**    | `catalog-of-life-macos.zip`    | LibreOffice Base or `mdbtools` |
| 🐧 **Linux**    | `catalog-of-life-linux.zip`    | `mdbtools`, SQLite, LibreOffice |
| 💻 **ChromeOS** | `catalog-of-life-chromeos.zip` | Crostini Linux container or web fallback |
| 🤖 **Android**  | `catalog-of-life-android.zip`  | AndrOpen Office / Google Sheets / Termux |
| 📱 **iOS**      | `catalog-of-life-ios.zip`      | Numbers / Excel + bundled HTML viewer |
| 🌐 **Web**      | `catalog-of-life-web.zip`      | Self-contained static site, runs from `file://` |

Per-platform install instructions live in [`docs/platforms/`](docs/platforms/).

## Compatibility matrix

| | Browse data | Run forms / queries | Run VBA / GEDCOM export |
|---|:---:|:---:|:---:|
| Windows + Microsoft Access | ✅ | ✅ | ✅ |
| macOS + LibreOffice Base   | ✅ | partial | ❌ |
| Linux + LibreOffice Base   | ✅ | partial | ❌ |
| Linux / macOS + `mdbtools` | ✅ (CLI) | ❌ | ❌ |
| ChromeOS + Crostini        | ✅ | partial | ❌ |
| Android + AndrOpen Office  | ✅ | ❌ | ❌ |
| iOS (CSV / JSON / viewer)  | ✅ | ❌ | ❌ |
| Web viewer                 | ✅ (sample data) | ❌ | ❌ |

> Microsoft Access remains the only platform on which the original VBA
> module (`Genealogy.ExportGED`) can run end-to-end. Every other platform
> ships pre-extracted data so the dataset is still usable.

## What's in this repository

```
.
├── Catalogue-of-Life-Converter-1.0.mdb   — original MS Access database
├── Catalogue-of-Life-Connection.png      — MySQL connection screenshot
├── INSTRUCTIONS.txt                      — original VBA build procedure
├── data/                                 — CSV exports of the small tables
├── docs/platforms/                       — per-platform install guides
└── web/                                  — static landing page + viewer
```

## Quick start

### Windows

```text
1. Install Microsoft Access 2007 or later (or the free Access Runtime).
2. Open Catalogue-of-Life-Converter-1.0.mdb.
3. Click "Enable Content" when the security warning appears.
```

See [`docs/platforms/windows.md`](docs/platforms/windows.md) for the full
GEDCOM-generation procedure.

### macOS / Linux

```sh
brew install mdbtools     # macOS
sudo apt install mdbtools # Debian / Ubuntu

mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb
mdb-export Catalogue-of-Life-Converter-1.0.mdb Top100 > Top100.csv
```

### Web (no install)

Open <https://socrtwo.github.io/catalog-of-life-SF/> — the bundled viewer
loads the sample dataset directly in the browser.

## How the GEDCOM is produced

The database links to a MySQL instance populated from a Catalogue of Life
annual checklist (Species 2000), then a VBA module walks the parent / child
graph and writes a GEDCOM file. The full procedure is in
[`INSTRUCTIONS.txt`](INSTRUCTIONS.txt). Output is ~2 million records covering
every species in the source dataset.

## Contributing

```sh
git checkout -b my-feature
# ... edits ...
git commit -m "Describe the change"
git push origin my-feature
# open a pull request
```

Issues and pull requests welcome at
<https://github.com/socrtwo/catalog-of-life-SF/issues>.

## Heritage

This project originated on **SourceForge** before being migrated to GitHub
with [SF2GH Migrator](https://github.com/socrtwo/sf-to-github). The
SourceForge entry, if still available:
<https://sourceforge.net/projects/catalog-of-life/>.

The repository here at `socrtwo/catalog-of-life-SF` is the canonical,
actively-maintained home.

## License

MIT — see [`LICENSE`](LICENSE).

---

*Maintained by [@socrtwo](https://github.com/socrtwo)*
