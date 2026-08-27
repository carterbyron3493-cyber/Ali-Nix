# alinixrealestate.com

Single-page marketing site for **Ali Nix**, real estate agent at More Agency (Tulsa, OK).
Built and maintained by Lobbii.

- **Live:** https://alinixrealestate.com
- **Netlify project:** `alinixrealestate.com`
- **Deploys:** GitHub → Netlify, on push to `main`

## Structure

```
index.html                  the entire site — markup, CSS and JS in one file
404.html                    branded not-found page
netlify.toml                publish dir, 404 redirect, cache + security headers
assets/listings/            10 property photos (for-sale + sold carousels)
assets/sold/                6 sold-badge photos
assets/portrait/            ali-hero.jpg, ali-about.jpg (1500x2000)
assets/og/og-cover.jpg      1200x630 link-preview card
assets/favicon/             favicon.svg + PNG fallbacks + apple-touch-icon
```

No build step on purpose. The HTML that ships is the HTML in the repo, so a
broken generator can never take the live site down. Edit `index.html`, commit,
push — Netlify does the rest.

## Details worth knowing

- **Fonts** are Fraunces (display), DM Sans (body) and Caveat (accent), loaded
  from Google Fonts. Nothing is self-hosted.
- **No forms.** Every call to action is a `tel:` or `mailto:` link. There is no
  Netlify Forms handler and no backend to break.
- **Contact of record:** 603-856-1858 · anix@moreagency.us · @mrsalinix
  These appear in the nav, hero, contact section, footer and the JSON-LD block.
  Change one, change them all — grep for the value.
- **Structured data** is a `RealEstateAgent` JSON-LD block at the end of `<head>`.
  Validate at https://search.google.com/test/rich-results after editing.
- **Link previews** come from `assets/og/og-cover.jpg`. If Ali's portrait
  changes, regenerate the card too or the preview goes stale.
- `assets/*` is cached immutable for 30 days by `netlify.toml`. Replacing a
  photo at the same filename needs a hard refresh (Cmd+Shift+R) to show up, or
  a new filename.

## History

Originally deployed by drag-and-drop (Netlify Drop). Moved onto this repo with
continuous deployment on 27 Aug 2026; the 18 images were recovered from the
live deploy at that time and are byte-identical to what was serving.
