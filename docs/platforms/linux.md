# Catalog of Life — Linux

## Option A — `mdbtools` (recommended for scripting)

`mdbtools` is the standard library for working with MS Access files on Linux.

```sh
# Debian / Ubuntu
sudo apt install mdbtools

# Fedora / RHEL
sudo dnf install mdbtools

# Arch
sudo pacman -S mdbtools

# List tables
mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb

# Export a single table to CSV
mdb-export Catalogue-of-Life-Converter-1.0.mdb Top100 > Top100.csv

# Export every table
for t in $(mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb); do
  mdb-export Catalogue-of-Life-Converter-1.0.mdb "$t" > "$t.csv"
done

# Convert the schema to PostgreSQL / MySQL / SQLite
mdb-schema Catalogue-of-Life-Converter-1.0.mdb postgres > schema.sql
```

### Loading into SQLite

```sh
# Schema
mdb-schema Catalogue-of-Life-Converter-1.0.mdb sqlite \
  | sqlite3 catalog-of-life.db

# Data
for t in $(mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb); do
  mdb-export -I sqlite Catalogue-of-Life-Converter-1.0.mdb "$t" \
    | sqlite3 catalog-of-life.db
done
```

## Option B — LibreOffice Base (GUI)

```sh
sudo apt install libreoffice-base
```

Then **File → Open** the `.mdb` file directly. Tables, queries and forms
are all browsable, but VBA modules cannot be executed.

## Option C — Run Access via Wine / a VM

- **Wine** — `winetricks access2010` (results vary)
- **VirtualBox / QEMU / KVM** with a Windows guest

Then follow the [Windows instructions](windows.md).

## Tested on

- Ubuntu 22.04 / 24.04
- Debian 12
- Fedora 40
- Arch Linux (rolling)
- mdbtools 1.0.0
