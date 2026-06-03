# reportwise-site

Static marketing + compliance site for ReportWise. Hosted on GitHub Pages at
`reportwise.codeblog.net`.

## Layout

- `index.html`, `privacy.html`, `terms.html`, `contact.html`, `404.html` —
  English at root, also duplicated under `en/` so the language switcher uses a
  consistent `/<lang>/...` URL shape.
- `zh/`, `zh-Hant/`, `ja/`, `de/`, `es/`, `fr/`, `pt-BR/`, `ko/`, `it/`, `nl/`,
  `hi/`, `id/`, `vi/` — one fully translated copy per language. 14 locales total,
  aligned with the app's supported locales.
- `assets/` — shared CSS, SVG illustrations, screenshots.
- `CNAME` — apex domain for GitHub Pages.
- `.nojekyll` — disable Jekyll processing.

Pages are pure HTML + CSS. No JavaScript, no build step.

## Editing flow

English is the source of truth. When you edit `en/<page>.html`:

1. Update the same page under each of the 13 other locale directories. Keep
   markup identical; only the visible text changes.
2. If you add or remove a section, mirror the change everywhere.
3. Update the `Last updated` line on `privacy.html` and `terms.html`.

The footer of each non-English page should keep the
`Machine-translated reference — English version controls.` note for legal text
(privacy, terms) to make the source-of-truth chain explicit.

## Deploy

1. Push to `main`.
2. On GitHub: Settings → Pages → Source: `Deploy from a branch` → `main` / root.
3. Custom domain: `reportwise.codeblog.net` (already in `CNAME`). Enforce HTTPS
   once the certificate is provisioned.

## Local preview

```sh
cd reportwise-site
python3 -m http.server 8000
# open http://localhost:8000/
```

## Related

- App + proxy: `~/Sync/Drop/vaulthealth/`
- API runs at `api.reportwise.codeblog.net`. The site does not call the API.
