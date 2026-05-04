# Catalog of Life — Android

There is no first-party Android port of Microsoft Access. The Android
release bundle therefore ships the database **plus pre-extracted CSV /
JSON exports** so the data is usable on any Android device.

## Option A — Open the CSV exports (no install)

The release bundle includes:

- `Top100.csv` — 100-row sample dataset
- `Top100family.csv` — parent / child relationships
- `kingdoms.csv` — Linnaean kingdoms
- `taxon_unit_types.csv` — taxonomic rank metadata
- `data.json` — the same data as JSON

These open in:

- **Google Sheets** (free, comes with most Android devices)
- **Microsoft Excel for Android**
- **WPS Office**, **OnlyOffice**, **Polaris Office**

## Option B — AndrOpen Office (works with the `.mdb` directly)

1. Install **AndrOpen Office** from
   [Google Play](https://play.google.com/store/apps/details?id=com.andropenoffice).
2. Open the bundle's `Catalogue-of-Life-Converter-1.0.mdb` file.
3. The data tables become browsable (forms / VBA do not run).

## Option C — Termux + mdbtools (power users)

1. Install [Termux](https://f-droid.org/en/packages/com.termux/) from F-Droid.
2. From the Termux prompt:

   ```sh
   pkg update && pkg install mdbtools
   termux-setup-storage
   cd ~/storage/downloads
   mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb
   mdb-export Catalogue-of-Life-Converter-1.0.mdb Top100
   ```

## Option D — Web viewer (no install)

Just open <https://socrtwo.github.io/catalog-of-life-SF/> in Chrome for
Android. The bundled viewer renders the dataset on any Android browser.

## Tested on

- Android 13 / 14 / 15 (Pixel 7, Galaxy S23)
- Google Sheets, Microsoft Excel, AndrOpen Office latest stable
