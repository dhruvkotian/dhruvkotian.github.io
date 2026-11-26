# dhruvkotian.dev

Personal site for **Dhruv Kotian**, a mechatronics engineering student working on embedded systems, edge AI and intelligent connected devices.

Live at **https://dhruvkotian.dev**

## How it is built

A single hand-written `index.html` with inline CSS and JavaScript:

- No frameworks, no build step, no trackers.
- **Three switchable pixel themes**, remembered in `localStorage` and applied before first paint:
  - **Ocean** (default): descends with scroll from bright surface water to mid-water, deep and abyss. Five stacked CSS gradient layers are cross-faded from `scrollTop`, with a fixed depth gauge on wide screens.
  - **Space**: a fixed starfield with twinkle and parallax, nebula washes, a ringed planet, satellite, rocket, lunar footer and a matching lavender/gold palette. The gauge switches from depth in metres to altitude in kilometres.
  - **Gothic**: a crypt of black, blood red and bone white, with a blood moon, skull, bats, an owl, a raven and a graveyard footer. An irregular web hangs at the top-left while a spider descends with scroll and stops on a tombstone. The spider and web are CSS-only. The gauge is hidden in this theme.
- A three-way pixel selector in the nav switches themes. It is a real radiogroup of buttons, so it works with the keyboard and announces its state.
- CSS-only light rays, rising bubbles, marine snow and scanlines. No canvas, no background images.
- Six pixel fish built from one SVG `<symbol>`, gliding on transform/translate animations. They fade in below the surface and are hidden under `prefers-reduced-motion`.
- **Themed sections carry a plain-language label** next to the heading (`Dive log / About`, `The wrecks / Projects`, `Cargo hold / Technical skills`), and the nav uses the plain terms. In space, the creative headings become `Flight log`, `The derelicts` and `Cargo bay`; in gothic they become `Blood ledger`, `The ossuary` and `Reliquary`. The brand reads `CRYPT`.
- **The wrecks and Research & Experiments are sliding decks**: each is a flex rail with `scroll-snap-type: x mandatory`, so it swipes on touch, scrolls on a trackpad, drags with a mouse, and steps with the arrow buttons, arrow keys or the dot row. One small initialiser drives both decks. No library, no per-frame JavaScript.
- Inline SVG pixel art: ocean sun, clouds, sailboat, coral and anglerfish; space planet, moon, satellite, rocket, lander and flag; gothic web, spider, blood moon, skull, bats, owl, raven and graves.
- Scroll work is deliberately small: layout is measured only on load, resize and theme change; the handler updates just the visible theme's layers; text and nav classes only change when their values change.
- Backgrounds are static gradients. Motion is limited to transform and opacity, so the browser can composite it instead of repainting the starfield.
- Photographs are local `webp` files in `img/`, 760 px wide (1800 px for the wide bench band), lazy-loaded.
- Two Google fonts (`Press Start 2P`, `VT323`); everything degrades to system monospace.

Total payload is roughly 135 KB of HTML plus ~450 KB of photos.

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
- Themes live on `<html data-theme="ocean|space|gothic">`. Space and gothic palette overrides sit in the `html[data-theme="space"]` and `html[data-theme="gothic"]` blocks; the selector stores its choice under the `dk-theme` key in `localStorage`.
- Theme-specific words use `data-ocean`, `data-space` and `data-gothic` attributes on the element (for example the brand and section headings). The switch script swaps the text without touching the markup.
- The gauge reads depth in ocean and altitude in space. Gothic hides it and keeps only the spider and web. Star parallax and the altitude value are updated in the same scroll handler as the ocean layers.
