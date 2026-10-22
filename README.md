# Read Along — public site

The public website for **Read Along**, a local-first read-aloud browser
extension. It is a plain static site: no build step, no framework, no external
requests.

The extension source lives in a separate, private repository. This repository
contains only the public pages and their assets.

## Pages

| File | Purpose |
| --- | --- |
| `index.html` | Landing page: features, screenshots, how it works, FAQ, availability |
| `support.html` | Install steps, shortcuts, troubleshooting, limits, contact |
| `privacy.html` | The privacy policy referenced by the Chrome Web Store listing |
| `changelog.html` | Release notes and planned work |
| `404.html` | Friendly not-found page |
| `assets/` | Stylesheet, small script, icon, screenshots, promo tile |
| `robots.txt`, `sitemap.xml` | Search-engine basics |

## Preview locally

```sh
cd read-along-site
python3 -m http.server 8080
```

Then open <http://localhost:8080>. Opening the HTML files directly also works,
but a server is closer to GitHub Pages.

## Deploy

The site is published with **GitHub Pages** from the `main` branch, repository
root. Pushing to `main` triggers a new deployment; no workflow file is needed
because the site is static and `.nojekyll` is present.

```sh
git add .
git commit -m "Update site"
git push
```

The public URL is <https://nayanbhut.github.io/read-along-site/>. GitHub Pages
usually deploys in under a minute. Check the **Actions** tab or the repository’s
**Settings → Pages** panel if a change does not appear.

### Custom domain (later)

If a domain is added, create a `CNAME` file with the domain, configure the DNS
records at the registrar, and enable **Enforce HTTPS** in Settings → Pages.
Update the canonical, Open Graph, sitemap, and robots URLs when that happens.

## Adding another page

1. Copy the header and footer from an existing page so the navigation matches.
2. Put the content in `<main id="main">`. Use the `.page-hero` and `.prose`
   classes for text pages.
3. Add the link to the header nav, the relevant footer column, and
   `sitemap.xml`.
4. Add a `<link rel="canonical">`, a `<title>`, and a meta description.
5. Preview at desktop and mobile widths before pushing.

## Keeping content accurate

- The privacy policy on `privacy.html` must match what the extension actually
  does. If the extension starts using cloud voices, update the policy **before**
  shipping that version.
- The store listing is in review at the time of writing. When it is approved,
  replace the “Coming soon” buttons with the real Chrome Web Store URL and update
  the FAQ/availability copy.
- Screenshots and the icon are copied from the extension repository’s `store/`
  folder. Regenerate them there when the UI changes, then copy them here.
- Do not add analytics, tracking pixels, external fonts, or third-party scripts.
  The “no cookies, no analytics” line in the footer should stay true.

## Contact

Questions about the site or the extension:
[nayanbhut989@gmail.com](mailto:nayanbhut989@gmail.com).
