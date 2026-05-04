# Catalog of Life — ChromeOS

ChromeOS supports Linux applications through the **Linux development
environment (Crostini)**, so the workflow mirrors [Linux](linux.md).

## One-time setup

1. Open **Settings → Advanced → Developers → Linux development environment**
   and click **Turn on**.
2. Wait for the VM to provision (~5 minutes).
3. Open **Terminal → penguin**.

## Install mdbtools

```sh
sudo apt update
sudo apt install mdbtools
```

## Open the database

Drag `Catalogue-of-Life-Converter-1.0.mdb` from **Files** into the
**Linux files** folder so the VM can read it, then:

```sh
cd ~/Linux\ files
mdb-tables -1 Catalogue-of-Life-Converter-1.0.mdb
mdb-export Catalogue-of-Life-Converter-1.0.mdb Top100
```

## GUI option — LibreOffice Base

```sh
sudo apt install libreoffice-base
libreoffice --base
```

Open the `.mdb` from inside Base; an icon will appear in the ChromeOS app
launcher under **Linux apps**.

## Web fallback — no Linux container

If your ChromeOS device does not support Crostini (managed devices, etc.):

1. Use the **bundled web viewer** — see [`web.md`](web.md).
2. Or open one of the CSV exports (`Top100.csv`, `kingdoms.csv`, …) in
   Google Sheets directly from **Files → Open with → Google Sheets**.

## Tested on

- ChromeOS 126 (Stable channel) on Acer Chromebook Spin 714
- ChromeOS Flex 126 on generic x86_64 hardware
