# BySide — marketing site

Single-page marketing site for **BySide**, a family-care service that looks after
parents in Kannur, Kerala for children who live away or don't have the time.

> When you can't be there, we are.

## Running it

There is no build step, no dependencies and no framework. It is one HTML file
plus a folder of images.

```bash
python3 -m http.server 8000
```

Then open <http://localhost:8000>. Opening `index.html` directly with `file://`
also works, but a local server matches production more closely.

## Deploying

Any static host will serve it as-is — GitHub Pages, Netlify, Vercel, Cloudflare
Pages, or plain nginx. Publish the repository root; there is nothing to compile.

## Structure

```
index.html     Everything: markup, CSS and JS, in that order
img/           Nine photographs, resized and compressed (~1.4 MB total)
```

Fonts (Newsreader, Karla, Noto Serif Malayalam) load from Google Fonts. Everything
else is self-contained.

## Before this goes live

- [ ] **Wire up the enquiry form.** It validates and shows a confirmation, but
      posts nowhere. Point it at Formspree, a serverless function, or your CRM —
      see the `form.enq` submit handler near the bottom of `index.html`.
- [ ] **Replace the placeholder content.** The names, reviews, star ratings, the
      phone number (+91 497 270 0700) and the Kannur address are all invented.
- [ ] **Replace the photography** with real pictures of your own companions and
      families. The current images are licensed stock (see Credits).
- [ ] **Make the social preview absolute.** `og:image` and `og:url` in `<head>`
      need full `https://` URLs once the domain exists.
- [ ] **Check the claims.** Response times, the 4.8 rating, "126 families" and
      the district roll-out dates are illustrative.

## Notes for whoever edits this next

- **Theming.** Colours are CSS custom properties defined once on `:root`, with a
  dark palette under `prefers-color-scheme: dark` and a `[data-theme]` override.
  Change a colour in one place, not twenty. Never define a colour only inside a
  media query.
- **Motion.** Scroll reveals are opt-in: JavaScript adds a `js` class to `<html>`
  only when `IntersectionObserver` exists and the visitor has not asked for
  reduced motion. Everything is visible at rest, and a 3-second failsafe releases
  anything the observer misses — so the page can never get stuck blank.
- **The map** in the coverage section is real geography: Kerala's fourteen
  district boundaries, projected and simplified from open GeoJSON. Kannur carries
  the `live` class. To open another district, move that class.
- **Accessibility.** Keyboard focus is visible, the carousel takes arrow keys, the
  comparison table uses proper row and column headers, and every image has alt
  text. Please keep it that way.

## Credits

Photography from [Pexels](https://www.pexels.com) under the Pexels licence (free
for commercial use, no attribution required — credited here anyway):

| File | Photographer |
| --- | --- |
| `amma.jpg` | Albin Biju |
| `achan.jpg` | Pareekshith Indeever |
| `hands.jpg` | Ekam Juneja |
| `kerala.jpg` | Gorky Sinha |
| `sadya.jpg`, `walk.jpg`, `companion.jpg`, `held.jpg`, `elder.jpg` | various, via Pexels |

District boundaries derived from the [india-maps-data](https://github.com/udit-001/india-maps-data)
GeoJSON collection.
