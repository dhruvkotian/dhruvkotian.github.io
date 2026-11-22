# dhruvkotian.dev

Personal site for **Dhruv Kotian**, a mechatronics engineering student working on embedded systems, edge AI and intelligent connected devices.

Live at **https://dhruvkotian.dev**

## How it is built

A single hand-written `index.html` with inline CSS and JavaScript:

- No frameworks, no build step, no trackers.
- **Pixel ocean theme** that descends with scroll: bright surface water, then mid-water, deep, and abyss. Five stacked CSS gradient layers are cross-faded from `scrollTop`, with a fixed depth gauge on wide screens.
- CSS-only light rays, rising bubbles, marine snow and scanlines. No canvas, no background images.
- Six pixel fish built from one SVG `<symbol>`, gliding on transform/translate animations. They fade in below the surface and are hidden under `prefers-reduced-motion`.
- **Themed sections carry a plain-language label** next to the heading (`Dive log / About`, `The wrecks / Projects`, `Cargo hold / Technical skills`), and the nav uses the plain terms.
- **The wrecks and Research & Experiments are sliding decks**: each is a flex rail with `scroll-snap-type: x mandatory`, so it swipes on touch, scrolls on a trackpad, drags with a mouse, and steps with the arrow buttons, arrow keys or the dot row. One small initialiser drives both decks. No library, no per-frame JavaScript.
- Inline SVG pixel art: sun, clouds, sailboat, coral, anglerfish.
- Photographs are local `webp` files in `img/`, 760 px wide (1800 px for the wide bench band), lazy-loaded.
- Two Google fonts (`Press Start 2P`, `VT323`); everything degrades to system monospace.

Total payload is roughly 76 KB of HTML plus ~450 KB of photos.

## Sections

| Section | Content |
|---|---|
| Surface | Name, tagline, status chips, links |
| 01 Dive log (About) | Biography, spec sheet, wide bench band |
| 02 The wrecks (Projects) | Eight project cards in a horizontal snap deck (ParoClaw, EM2M, HyperWatch, AI Tunnel Fan, AI EV BMS, Pi Camera, Semi-Humanoid, Mobile Manipulator) |
| 03 Research & Experiments | Three research cards in a horizontal snap deck (Vacuum Plasma Chamber, ESP32-S3 Native Linux SDMMC, DC Fan Vibration Monitor) |
| 04 Cargo hold (Technical skills) | Languages, embedded, edge AI, connectivity, bench skills |
| Seafloor | Contact links (LinkedIn, GitHub, ORCID) and colophon |

## Deploying

GitHub Pages serves the `master` branch from `/`. Push to `master` and the site rebuilds automatically:

```sh
git add index.html img README.md
git commit -m "Update site"
git push origin master
```

`CNAME` pins the custom domain to `dhruvkotian.dev`.

## Editing

- Biography, project cards and stack chips all live in `index.html`.
- Project cards are `<article class="card">` blocks inside `#projectRail`, in deck order. Add or remove one and the counter and dots follow automatically.
- Cards use `.card-media` with a local photo and a pixel captions; every project has one.
- The wide band under the about grid is `figure.workbench`.
- The depth cross-fades are computed in the first `<script>` block (`ramp()` calls). Adjust the numbers to change where each water layer takes over.
