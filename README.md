# Million Times Clock

A generative clock art piece: a grid of hundreds of tiny analog clocks, each one
individually posed so that together they spell out the current time.

<video controls muted loop playsinline width="720">
  <source src="https://github.com/Hammad-Infinity/Million-Times-Clock/raw/main/docs/demo.webm" type="video/webm">
  <source src="https://github.com/Hammad-Infinity/Million-Times-Clock/raw/main/docs/demo.mp4"  type="video/mp4">
</video>
<picture>
  <source srcset="docs/preview.avif" type="image/avif">
  <img src="docs/preview.png" alt="Million Times Clock preview">
</picture>

Watch Demo here [Demo](http://hammad-infinity.github.io/Million-Times-Clock/)
Built with nothing but HTML, CSS, and vanilla JavaScript — no build step, no
dependencies, no framework.

---

## What it does

Every cell in the grid is a real two-hand clock. The hands rotate to preset
angles so that a cell can represent a "pixel" of a larger glyph. By arranging
those glyphs across the grid, the display can spell digits, letters, the
current time, and a rotating set of 22 animated patterns.

- **Time mode** — shows HH:MM (and seconds when the grid is large enough), plus
  a day/date strip underneath.
- **Portrait mode** — when the grid is taller than it is wide, hours and minutes
  stack vertically for larger digits.
- **Scroll mode** — a random stream of letters that scrolls across the grid.
- **20 procedural patterns** — radial vectors, vortex fields, spirals, rings,
  pinwheel, burst, figure-8, crosshatch, and more, all animated smoothly.

---

## Features

| Feature | Notes |
|---|---|
| Adjustable grid | 8–24 columns, 3–14 rows, live preview |
| Auto-fit | Cell size scales to the largest grid that fits the window |
| 12 / 24-hour | Toggle at runtime |
| Dark / Light theme | Smoothly interpolated color transitions |
| Mouse follow | Every hand tracks the cursor with easing |
| Ripple click | Clicking the canvas sends an angle ripple outward |
| Transition speed | 1–20 s slider for pattern-to-pattern animation |
| Fullscreen | Press **F** to toggle (not listed in the UI) |
| Draggable HUD | Settings button snaps to the nearest left/right edge |
| Persistent | Theme and grid size are remembered in `localStorage` |

---

## How it works

### Cells are clocks

Each cell is drawn as a small clock face with two hands:

- **Hand A** — long (`0.95 × radius`)
- **Hand B** — short (`0.85 × radius`)

Angles are in degrees, where `0 = up`, `90 = right`, `180 = down`, `270 = left`
(clockwise because canvas rotation is clockwise).

### Glyphs are pose grids

A glyph is a 2-D array of *state indices* into a shared pose table
(`clockStates`). Index `12` is the "blank" pose `(225°, 225°)`, used to clear a
cell. Converting a glyph to angles is a single table lookup.

- **Digit sets**: `2x3, 2x4, 2x5, 3x4, 3x5, 3x6` (width × height). Each is a
  set of ten grids, one per digit.
- **Letters**: fixed 4 × 6 grids, A–Z.
- **Overrides**: `handEdits` re-styles specific glyphs by supplying exact
  `[angleA, angleB]` pairs (used to fix R, M, W, Q, X, Z, A, B, G, K, N, V, Y).

### Layout search picks the scale

`searchTimeLayout` brute-forces every combination of glyph set, format
(`hms`, `hm`, plain variants), colon width, and inter-digit gap that fits the
grid. Candidates are ranked lexicographically:

1. colons present → 3-wide digits → hms over hm → wider colon → taller glyph → gap

`chooseTimeLayout` adds a portrait check first: if `rows > cols`, it looks for
the largest glyph set that can stack hours over minutes with one blank row
between them.

### Animation is per-cell

The `Clock` class holds `angleA/B`, `animA/B`, and `alphaA/B`. When a target is
set:

- Rotation always takes the **shortest angular path**.
- Alpha fades use `smoothStep`, rotation uses linear interpolation.
- A `null` target fades the hand out and parks it at the rest angle.

Resizing the grid preserves existing `Clock` instances, so hands keep their
current angles across column/row changes.

### Rendering

The clock face is a radial gradient rendered **once** into an offscreen canvas
and blitted per cell. Hands and hubs are drawn on top. Ripples are additive
angle offsets applied at draw time.

---

## Getting started

No build step. Just open `Million_Times_Clock.html` in a browser.

```bash
git clone https://github.com/Hammad-Infinity/Million-Times-Clock.git
cd Million-Times-Clock
open Million_Times_Clock.html   # macOS
# or: xdg-open Million_Times_Clock.html   # Linux
# or: start Million_Times_Clock.html      # Windows
```

Or serve it locally if you prefer:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/Million_Times_Clock.html
```

---

## Controls

| Control | Where | Effect |
|---|---|---|
| Theme pill | Settings header | Dark / Light |
| Columns slider | Settings | Grid width (8–24) |
| Rows slider | Settings | Grid height (3–14) |
| Speed slider | Settings | Pattern transition duration (1–20 s) |
| Show time | Settings | Jump to the live clock |
| 24-hour | Settings | Toggle 12/24-hour display |
| Mouse follow | Settings | Hands track the cursor |
| **F** key | Anywhere | Toggle fullscreen |
| Click canvas | Anywhere | Spawn a ripple from that cell |
| Drag the HUD | Settings button | Snap panel to left or right edge |

---

## Browser support

Requires a modern evergreen browser with:

- Canvas 2D (`globalCompositeOperation`, `createRadialGradient`)
- Pointer Events
- Fullscreen API (for the **F** shortcut)
- `localStorage` (for persistence; degrades gracefully)

Tested on current Chrome, Firefox, Safari, and Edge.

---

## Project structure

```
Million_Times_Clock.html   Single-file app: styles, markup, and script
README.md                  This file
docs/                      Screenshots and demo media (see below)
```

The app is intentionally a single file. Everything else is documentation.

---

## Adding media to this README

A picture is worth a lot here, because the project is visual. Three options,
in order of effort:

### 1. Static screenshot (easiest)

1. Open the app, set the theme and grid you want.
2. Take a screenshot (`Win+Shift+S` / `Cmd+Shift+4` / your OS tool).
3. Save it as `docs/preview.png` in the repo.
4. Reference it at the top of this README:

   ```markdown
   ![Million Times Clock](docs/preview.png)
   ```

GitHub renders this inline. PNG or JPG both work; keep it under ~1 MB so the
page loads fast.

### 2. Animated GIF (best for showing motion)

1. Record a short clip (5–10 s) of a pattern transition, using OBS, LICEcap,
   or your OS recorder.
2. Convert to GIF with `ffmpeg`:

   ```bash
   ffmpeg -i capture.mp4 -vf "fps=15,scale=800:-1:flags=lanczos" \
     -loop 0 docs/preview.gif
   ```

   Aim for **under 10 MB** — GitHub will serve it inline but large GIFs load
   slowly and may not autoplay well on mobile.

3. Reference it the same way:

   ```markdown
   ![Million Times Clock](docs/preview.gif)
   ```

### 3. Embedded video (nicest for a long demo)

GitHub renders `.mp4` and `.webm` files dragged directly into an issue or PR
comment, but **not** in a README. Two workarounds:

**A. Link to a hosted video with a clickable thumbnail** (recommended):

```markdown
[![Watch the demo](docs/preview.gif)](https://youtu.be/YOUR_VIDEO_ID)
```

The GIF acts as the thumbnail; clicking opens the video.

**B. Use the `<video>` tag with a raw URL** (works on github.com, not always
in third-party renderers):

```html
<video src="https://github.com/USER/REPO/raw/main/docs/demo.mp4"
       controls muted loop playsinline width="720"></video>
```

For this to work, commit `docs/demo.mp4` to the repo. Keep it under ~25 MB —
GitHub has a 100 MB per-file limit, but large files bloat clone size. For
anything longer than a few seconds, host on YouTube or Vimeo and use option A.

### Sizing tips

- Record at the grid size you want people to see (24 × 12 is the default and
  looks good).
- Trim before converting — every extra second of GIF costs megabytes.
- Use `scale=800:-1` for GIFs so they fit in the README column without
  downscaling artifacts.
- If you add a screenshot **and** a GIF, put the GIF first — it tells the story.

---

## Credits

Built by [Hammad](https://github.com/Hammad-Infinity).

---

## License

- The GNU Affero General Public License (AGPL).
