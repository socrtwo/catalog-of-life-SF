# Catalog of Life — Web

The repository ships a static, JavaScript-only viewer that runs in any
modern browser without server-side code.

## Hosted

🌐 <https://socrtwo.github.io/catalog-of-life-SF/>

The site is automatically rebuilt on every push to `main` and on every
GitHub release by the [`pages.yml`](../../.github/workflows/pages.yml)
workflow.

## Running locally

The Web release bundle (`catalog-of-life-web.zip`) is a self-contained
static site:

```sh
unzip catalog-of-life-web.zip -d col-web
cd col-web
python3 -m http.server 8000
# open http://localhost:8000/
```

Or simply double-click `index.html` — the viewer works from `file://` too.

## What's included

- `index.html` — landing page that renders the README and exposes
  download links for every platform release
- `viewer.html` — interactive table browser (filter, sort, kingdom
  breakdown) for the bundled dataset
- `data.json` — the `Top100`, `Top100family`, `kingdoms`, and
  `taxon_unit_types` tables, ready to consume from JS
- `*.csv` — same data as plain CSV

## Embedding the dataset in another project

```html
<script type="module">
  const data = await fetch(
    'https://socrtwo.github.io/catalog-of-life-SF/data.json'
  ).then(r => r.json());
  console.log(data.kingdoms);   // ['Animalia', 'Archaea', ...]
  console.log(data.Top100[0]);  // { individual: 2, "given-name": ..., ... }
</script>
```

## Browser support

- Chrome / Edge 90+
- Firefox 90+
- Safari 14+
- Mobile Safari, Chrome for Android
