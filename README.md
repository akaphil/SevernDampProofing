# Severn Damp Proofing — severndampproofingltd.com

Conventional damp-proofing website for **Severn Damp Proofing Ltd** (Gloucestershire & the Cotswolds).
Sister site to the heritage-lime brand [severnlime.co.uk](https://severnlime.co.uk).

Static [Hugo](https://gohugo.io) site, deployed on Cloudflare Pages. No backend — phone/email lead capture only.

## Positioning

Honest, diagnosis-led damp specialist: rising damp / DPC, basement & cellar tanking, penetrating damp,
condensation & mould, timber treatment. Deliberately distinct from severnlime (which owns the *breathable /
heritage* lime work) so the two brands don't compete for the same search terms.

## Structure

```
hugo.yaml                 # config: baseURL, company params, SEO defaults
content/                  # flat pages, rendered by the theme's _default/single.html
  services.md             # /services/  (overview)
  rising-damp.md          # /rising-damp/
  basement-tanking.md     # /basement-tanking/
  damp-survey.md          # /damp-survey/
  areas.md                # /areas/
  about.md                # /about/
  contact.md              # /contact/
layouts/robots.txt        # declares the sitemap
themes/craftsman/         # copied from the severnlime project, recoloured
  static/css/main.css     #   :root palette = protective blue / cool neutrals
  layouts/index.html      #   damp-specific home page
  layouts/partials/*      #   header/footer/floating-contact rewritten for damp
static/images/            # logos + damp/property photos
```

The home page is `themes/craftsman/layouts/index.html`; every other page is a Markdown file in `content/`
rendered by `themes/craftsman/layouts/_default/single.html`.

## Develop

```bash
hugo server          # http://localhost:1313
hugo --gc --minify   # production build into public/
```

## Deploy (Cloudflare Pages)

1. Connect this repo → framework **Hugo**, build command `hugo --gc --minify`, output `public`.
2. Set env var `HUGO_VERSION` (e.g. `0.154.5`).
3. Add custom domain `severndampproofingltd.com` (apex) + a **www → apex** Redirect Rule.
4. Submit `https://severndampproofingltd.com/sitemap.xml` in Search Console; request indexing for key pages.

## SEO notes (lessons from severnlime)

- `baseURL` is the apex (non-www); `relativeURLs: false` (absolute URLs).
- `robots.txt` declares the sitemap; every page has a unique title/description and self-canonical.
- Keep content **distinct** from severnlime — never copy pages between the two sites.
