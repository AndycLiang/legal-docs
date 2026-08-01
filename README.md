# legal-docs

Public legal documents (privacy policies, terms of service) for our apps,
served as a static site via **GitHub Pages** (Jekyll).

## Live site

Once Pages is enabled, docs are available at stable URLs, e.g.:

- `https://<user>.github.io/legal-docs/` — index of all apps
- `https://<user>.github.io/legal-docs/flockle/privacy/`
- `https://<user>.github.io/legal-docs/flockle/terms/`

These are the URLs to paste into App Store Connect / Google Play and the app UI.

## Enable GitHub Pages (one time)

In the GitHub repo: **Settings → Pages → Build and deployment → Source: Deploy
from a branch**, choose branch `main` and folder `/ (root)`, then **Save**.
No GitHub Actions workflow is required — Pages builds the Jekyll site for you.

## Repository layout

```
_config.yml        Site config (title, clean URLs, defaults)
_data/apps.yml     Registry of apps + their docs (drives the home page)
_layouts/doc.html  Shared HTML layout + styling for every page
index.md           Home page (lists apps from _data/apps.yml)
flockle/           One folder per app, holding its Markdown docs
  PRIVACY.md
  TERMS.md
  SUPPORT.md
revel/
  GUIDELINES.md
```

## Adding a new app

1. Create a folder for the app (e.g. `revel/`).
2. Add each document as a Markdown file with front matter setting a `title`
   and a `permalink`, for example:

   ```markdown
   ---
   title: Revel Privacy Policy
   permalink: /revel/privacy/
   ---

   # Revel Privacy Policy
   ...
   ```

3. Register the app in `_data/apps.yml` so it shows on the home page:

   ```yaml
   - name: Revel
     slug: revel
     tagline: Short description.
     docs:
       - title: Privacy Policy
         url: /revel/privacy/
       - title: Terms of Service
         url: /revel/terms/
   ```

The `url` in `apps.yml` must match the document's `permalink`.

## Preview locally (optional)

```bash
gem install bundler jekyll
jekyll serve   # then open http://localhost:4000/legal-docs/
```
