# Inkwork Press

Turns a PNG into a black-and-red ornamental ink illustration: patterned parts, fine outlines, one red sun and textured paper.

It is a single static file, `index.html`, with no build step, no server code and no AI. All processing happens in the visitor's browser, so images never leave their device.

## Run it locally

Double-click `index.html`, or serve the folder:

```bash
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

Upload `index.html` to any static host: GitHub Pages, Netlify, Vercel, Cloudflare Pages or your own server. Nothing else is needed. It loads its fonts from Google Fonts; without a connection it falls back to system fonts.

## How it works

1. **Cut out** – uses the PNG's transparency, or removes a plain background by flood fill from the edges.
2. **Split into parts** – smooths the image, groups pixels by tone and colour (k-means), then merges small fragments.
3. **Pattern and line** – fills each part with a pattern chosen by its tone (solid, contour lines, border bands, scallops, dots and more), adds an inner rim, part outlines and a heavier silhouette.
4. **Red and paper** – adds the red circle and any parts clicked red, then prints everything onto a generated watercolour-paper texture.

The interface is dark by default; the sun/moon button in the header switches to light, and the choice is remembered in that browser.

Controls: tone levels, merge size, pattern density, darkness, line weight, inner detail, inner rim, ink colour, red circle size and position, paper colour and grain. Click a part of the drawing to paint it red, or switch to "Change its pattern" and click to step that part through the 23 patterns.

## Downloads

- **PNG** – the finished illustration on its paper background.
- **Transparent PNG** – ink and red only, no paper.
- **SVG** – editable vectors in three layers: `paper` (the texture as an embedded image), `red` (the circle and red parts) and `ink` (patterns and lines). Paper grain inside the ink and red is flattened to solid colour.
