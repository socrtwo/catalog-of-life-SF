# Catalog of Life — Windows

The reference platform. The `.mdb` is an MS Access 2000/2003 database, so it
opens natively on Windows.

## Option A — Microsoft Access (full functionality, including VBA / GEDCOM export)

1. Install **Microsoft Access 2007 or later** (or the free
   [Access Runtime](https://www.microsoft.com/download/details.aspx?id=50040)
   if you only need to view).
2. Double-click `Catalogue-of-Life-Converter-1.0.mdb`.
3. Click **Enable Content** when the security warning appears (the file
   contains the `Genealogy` VBA module that performs the GEDCOM export).
4. To regenerate the database with current Catalogue of Life records, follow
   the procedure in `INSTRUCTIONS.txt` at the repository root.

## Option B — MDB Viewer Plus (read-only, no install)

If you only want to browse the tables, queries and forms:

1. Download **MDB Viewer Plus** from <https://www.alexnolan.net/software/mdbplus.htm>.
2. File → Open → select `Catalogue-of-Life-Converter-1.0.mdb`.
3. Tables of interest: `Top100`, `Top100family`, `kingdoms`, `parent`,
   `taxon_unit_types`.

## Producing the GEDCOM file

Inside Access:

1. Open the **Genealogy** VBA module (`Alt+F11`).
2. Edit the `sFile` variable to your desired output path.
3. Set `bTesting = False` for the full 2-million-record export, or `True`
   for the 100-row sample.
4. In the Immediate Window (`Ctrl+G`) type `ExportGED` and press **Enter**.

## Tested on

- Windows 10 / 11 with Access 2016, 2019, 2021, and Microsoft 365.
