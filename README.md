# Law Office of Shawn McKenna — website

A single-request static website for a Chicago divorce and family law practice.
`index.html` is the entire site: markup and critical CSS in one file, with no
framework, bundler, web font, JavaScript, or third-party request. It gzips to
about 10 KB, which fits inside a single TCP round trip, so the page paints as
soon as the first packet lands.

## Verify before publishing

The build environment blocked `lawfirmfordivorce.com` and `shawnlawgroup.com`,
so the firm details on this page came from **web search results, not from the
firm's own pages**. Confirm each before it goes live:

- Practicing family law exclusively since 2009
- LL.M. in Family Law, Chicago-Kent College of Law
- Super Lawyers "Rising Star," Family Law, each year since 2019
- Chicago office at 105 W. Madison St., Suite 1300, Chicago, IL 60602
- Phone (312) 806-5347; Monday-Friday, 9:00-5:00
- Free initial in-office consultation

Then search `index.html` for `TODO:` and fill in what is still missing: the
Rolling Meadows address, the firm email, bar admissions, education, the
canonical domain, the copyright year, and two or three sentences of personal
background in the attorney section. Delete the `.todo` CSS rule and the
verification comment block at the top of the file when done.

### Advertising rules

The page is written to stay inside Illinois Rules of Professional Conduct
7.1-7.3: no client testimonials, no past results, no superlatives, and no
language creating an expectation about outcomes. The Super Lawyers reference
names the organization conferring it and is paired with a footer statement that
ratings do not guarantee a result — confirm that satisfies current ARDC
guidance. An "Attorney advertising" notice and a no-attorney-client-relationship
statement are both present.

Practice-area copy describes the Illinois statutory framework in general terms
and cites the governing statutes. Confirm the citations still read the way the
page describes them, and re-check when the statutes change.

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
