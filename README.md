# dhruvkotian.dev

Personal site for **Dhruv Kotian** — mechatronics engineering student working on embedded systems, edge AI and intelligent connected devices.

Live at **https://dhruvkotian.dev**

## How it is built

A single hand-written `index.html` with inline CSS and JavaScript:

- No frameworks, no build step, no images, no trackers.
- Retro-pixel space theme using the HyperLife palette, rendered with CSS gradients and an inline SVG astronaut.
- CSS-only starfield and scanlines, scroll progress bar, and `IntersectionObserver` reveal animations.
- Two Google fonts (`Press Start 2P`, `VT323`); everything degrades to system monospace.

Total payload is roughly 33 KB of HTML.

## Deploying

GitHub Pages serves the `master` branch from `/`. Push to `master` and the site rebuilds automatically:

```sh
git add index.html
git commit -m "Update site"
git push origin master
```

`CNAME` pins the custom domain to `dhruvkotian.dev`.

## Editing

All content — biography, project cards, stack chips — lives in `index.html`. Project cards are `<article class="card">` blocks inside `#projects`; the stack columns are `.stack-col` panels inside `#stack`.
