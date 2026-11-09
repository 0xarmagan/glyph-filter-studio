# Glyph Filter Studio

Turn any image or geometric figure into a glowing matrix of tiny pixel glyphs. It runs entirely in the browser, with no build step and no dependencies.

Open `index.html` (or the Vercel deployment). It starts on the EEZ mark, rendered for a light ground. Upload, drag or paste an image to filter your own.

## How the filter works

1. **Source.** For an image, average the brightness of each 9×10 px cell and apply black point, white point and gamma. For a built-in shape, draw it in three layers: a wide soft falloff, the band, and a thin bright core.
2. **Glyphs.** Replace each cell with a 6×8 pixel glyph chosen by brightness. In order: dot, colon, bracket, small box, box, box with a core, solid box.
3. **Light.** Colour each glyph from a gradient using its brightness, a directional light term and an edge (rim) term. You can also keep the image's own colours.
4. **Warp.** Domain-warp the field with value noise plus a slow wobble, drop random glyph pixels, trail vertical streaks up and down from the outermost strokes, and scatter square sparks around the figure.
5. **Bloom.** Lay a blurred colour glow under the glyphs and a 2 px bloom of the glyphs over them, both blended additively.

## Controls

- **Source:** your image, the EEZ mark, or the built-in shapes (diamond, cube, circle, triangle, hexagon, square, lines, line, vertical bar, horizontal bar).
- **Build-up:** passes 01–05.
- **Palette:** EEZ, electric, brand, ember, mono, or the image's colours.
- **Filter:** size, cell, density, warp, wobble, streaks, sparks, dot columns, glow.
- **Levels and light:** black point, white point, gamma, edge boost, light amount, light angle.
- **Ground:** light (glyphs painted as ink on paper) or dark (glyphs added as light).
- **Background:** solid, a custom colour, or transparent.
- **Export:** PNG at 1×, 2× or 3×. The export is drawn again at that scale, so the glyphs stay crisp.

## Repository layout

- `index.html`: the standalone app.
- `design/glyph-figure.js`: the renderer used for the shapes and separators.
- `design/*.dc.html`: the Design canvas artboards: playground, technique breakdown, figures, partner banner with a glyph divider, and separators.
