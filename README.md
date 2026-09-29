# sisyphe

Company site for Sisyphe LLC ("AI that acts in the world"). Quarto, static, no execution at render time. The founder's employer is deliberately never named on the site.

## Pages

| File | Page |
|---|---|
| `index.qmd` | Thesis, the perceive–reason–act loop, proof strip, products, founder teaser |
| `sideman.qmd` | Sideman product summary; the full landing page stays with the code |
| `course.qmd` | The ten-lesson course |
| `work.qmd` | Services and proof |
| `instruments.qmd` | Lineage: a timeline of situated systems from 2007 to now |
| `about.qmd` | Founder and company |

## Render

```bash
quarto preview      # live at http://localhost:4200-ish
quarto render       # writes _site/
```

## Deploy

`.github/workflows/pages.yml` renders and publishes to GitHub Pages on every push to `main`. In the repo settings, set Pages → Source to **GitHub Actions** once.

## Domain

`sisyphe.ai` is registered by someone else (checked 2026-09-28). `site-url` in `_quarto.yml` is the GitHub Pages URL until a domain is chosen. When one is, change `site-url`, add a `CNAME` file containing the bare domain at the repo root, and list it under `project.resources` in `_quarto.yml` so Quarto copies it into `_site`.

## SEO

Quarto emits title/description, Open Graph and Twitter cards, `sitemap.xml` and `robots.txt`. On top of that: `_seo.html` adds JSON-LD (Organization, founder Person, Sideman SoftwareApplication) to every page's head, and `assets/brand/og.png` (1200×630, dark card with the loop) is the site-wide share image, forced on pages that contain a photo via `image:` front matter. Regenerate the card from the scratch HTML in the session notes if the tagline changes. Update the URLs in `_seo.html` when the domain changes.

## Analytics

Cloudflare Web Analytics, via `_analytics.html`, included in every page's `<head>`. It sets no cookies, so no consent banner. Create the site under Analytics & Logs → Web Analytics in the Cloudflare dashboard (any hosting, not only Cloudflare Pages), copy the token from the snippet it shows, and replace `REPLACE_WITH_CLOUDFLARE_TOKEN` in `_analytics.html`. Until then the beacon loads with a bogus token and records nothing.

## Theme

`theme.scss` (light) and `theme-dark.scss` (dark, the default) share Sideman's design tokens (Bricolage Grotesque, IBM Plex, accent `#D9432B` / `#FF6B52`, warm grey grounds) plus three layer colours for perceive, reason and act taken from Sideman's clip palette.
