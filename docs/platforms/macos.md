# Catalog of Life — macOS

Microsoft Access has no native macOS build, so use one of the routes below.

## Option A — LibreOffice Base (recommended, free)

1. Install **LibreOffice** from <https://www.libreoffice.org/download/> or via
   Homebrew: `brew install --cask libreoffice`.
2. Open LibreOffice Base.
3. **File → New → Database → Connect to existing database → Microsoft Access**
   and pick `Catalogue-of-Life-Converter-1.0.mdb`.
4. The tables (`Top100`, `kingdoms`, `parent`, etc.) are now browsable.

> Note: LibreOffice can read the data but cannot run the original VBA
> (`Genealogy`) module. Use Option B or the bundled CSV / JSON exports
> if you need the GEDCOM output.

## Option B — `mdbtools` (command line)

```sh
brew install mdbtools

# List tables
mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb

# Export every table to CSV
for t in $(mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb); do
  mdb-export Catalogue-of-Life-Converter-1.0.mdb "$t" > "$t.csv"
done

# Dump the schema as SQL
mdb-schema Catalogue-of-Life-Converter-1.0.mdb mysql > schema.sql
```

## Option C — Run Access in a VM

If you need the full VBA / GEDCOM export, run Windows in:

- **UTM** — <https://mac.getutm.app/> (free, Apple Silicon and Intel)
- **Parallels Desktop** — <https://www.parallels.com/>
- **VMware Fusion** — <https://www.vmware.com/products/fusion.html>

Then follow the [Windows instructions](windows.md).

## Tested on

- macOS 13 Ventura, 14 Sonoma, 15 Sequoia (Intel and Apple Silicon)
- LibreOffice 7.6 / 24.8
- mdbtools 1.0.0
