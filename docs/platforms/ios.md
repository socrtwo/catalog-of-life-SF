# Catalog of Life — iOS / iPadOS

There is no native MS Access viewer for iOS. The iOS release bundle ships
**CSV / JSON exports** and a self-contained **HTML viewer** that runs in
Safari without any install.

## Option A — Open the CSV exports

The bundle contains:

- `Top100.csv`, `Top100family.csv`, `kingdoms.csv`, `taxon_unit_types.csv`
- `data.json`

These open natively in:

- **Numbers** (free, pre-installed)
- **Microsoft Excel**, **Google Sheets**, **WPS Office**

Save the bundle to **Files → On My iPhone / iCloud Drive** and tap any CSV.

## Option B — Built-in HTML viewer

Inside the iOS release bundle there is a `viewer/` directory containing a
self-contained, JavaScript-only browser for the dataset. Tap
`viewer/index.html` to open it in Safari — no network connection or
install required.

## Option C — Web viewer (no install, no download)

Open <https://socrtwo.github.io/catalog-of-life-SF/> in Safari. Works on
any iPhone or iPad running iOS 13+.

## Producing the GEDCOM file on iOS

The original GEDCOM export requires Microsoft Access VBA, which is not
available on iOS. Two options:

1. Run Access in a Windows VM (e.g. via **UTM SE**) and follow the
   [Windows instructions](windows.md).
2. Use the GEDCOM file produced on a desktop platform; the bundled
   `data.json` can also be transformed to GEDCOM with any third-party
   converter.

## Tested on

- iOS 17 / 18 (iPhone 14, iPhone 15)
- iPadOS 17 / 18 (iPad Air 5, iPad Pro M4)
- Safari, Chrome, Firefox for iOS
