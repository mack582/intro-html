# Law Office of Shawn McKenna — website

A single-request static website for a Chicago divorce and family law practice.
`index.html` is the entire site: markup and critical CSS in one file, with no
framework, bundler, web font, JavaScript, or third-party request. It gzips to
about 7 KB, which fits inside a single TCP round trip, so the page paints as
soon as the first packet lands.

## Before publishing

The site ships with every firm-specific fact left blank on purpose. Nothing
about credentials, experience, results, or clients has been written for you,
because those are claims only the firm can make accurately.

Search `index.html` for `TODO:` and fill in:

1. Phone number, email address, and office address (including the `tel:` and
   `mailto:` hrefs, which are intentionally empty).
2. Office hours, and whether the initial consultation is free or its fee.
3. The "About the firm" paragraph — admissions, year of licensure, education,
   background, and how the practice is run.
4. The copyright year and any disclosure required by the Illinois Rules of
   Professional Conduct.

Then delete the `.todo` CSS rule and the placeholder comment block at the top
of the file.

### Advertising rules

The page is written to stay inside Illinois Rules of Professional Conduct
7.1–7.3: no client testimonials, no past results, no superlatives, no
comparative claims, and no language creating an expectation about outcomes. It
carries an "Attorney advertising" notice and a statement that contacting the
firm does not create an attorney-client relationship. Anything you add should
be measured against those rules before it goes live.

Practice-area copy describes the Illinois statutory framework in general terms
and cites the governing statutes. Confirm the citations still read the way the
page describes them before publishing, and re-check when the statutes change.

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
branch** and pick your branch with the `/ (root)` folder.

Use a real domain rather than the `github.io` URL for a firm site, and note
that a public GitHub repository makes the source visible to anyone.

## Performance budget

Keep these and the site stays quick as it grows:

- One request for first paint — the HTML carries its own styles.
- No render-blocking resources; anything optional loads lazily or not at all.
- Images in a modern format with explicit `width`/`height` and `loading="lazy"`.
- Initial document under 14 KB compressed.
- No dependency, analytics tag, or embedded widget added without a measurement
  of what it costs — in speed and in what it discloses about visitors, who on a
  family law site are often in a sensitive situation.

---

This repository began as a GitHub Learning Lab repository for Intro to HTML and
is licensed under [MIT](LICENSE) (c) 2019 GitHub, Inc.
