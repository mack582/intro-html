# intro-html

A hand-written static website that loads in a single request.

`index.html` is the whole site: markup and critical CSS in one file, with no
framework, bundler, web font, script, or third-party request. It gzips to about
4 KB, which fits inside a single TCP round trip, so the browser paints as soon
as the first packet lands.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The site. Inlined CSS, no JavaScript, light and dark themes. |
| `404.html` | Not-found page, styled to match. GitHub Pages serves it automatically. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is instead of running Jekyll. |

## Preview locally

```
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Opening `index.html` directly in a browser
works too — there is no build step.

## Deploy

Push the branch, then in the repository go to **Settings → Pages → Deploy from
branch** and pick your branch with the `/ (root)` folder. GitHub serves it over
its CDN within a minute or so.

## Performance budget

Keep these and the site stays quick as it grows:

- One request for first paint — the HTML carries its own styles.
- No render-blocking resources; anything optional loads lazily or not at all.
- Images in a modern format with explicit `width`/`height` and `loading="lazy"`.
- Initial document under 14 KB compressed.
- No dependency added without a measurement of what it costs.

---

Originally a GitHub Learning Lab repository for Intro to HTML.

This repository is licensed under [MIT](LICENSE) (c) 2019 GitHub, Inc.
Photo by [Kelli Tungay](https://unsplash.com/photos/Sj0nhVIb4eY) on [Unsplash](https://unsplash.com/)
