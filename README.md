# Letterloop

**Type anything and it wraps into an organic frame of letters.**

Letterloop is a small browser tool for making typographic frames: a wobbly, hand-shaped loop of letters that bump into and overlap each other, like a riso-printed event poster. You can reshape the frame by dragging its points, pick a typeface and colors, apply letter effects, and place your own image inside. When it looks right, export a high-resolution PNG.

It's a single HTML file with no build step, no framework and no install.

## Features

**Frame**
- Organic outline generated from a few control points, with sliders for point count, wobble and softness
- Drag points on the canvas to reshape it. Double-click the outline to add a point, or double-click a point to remove it
- Scale, rotate and move the frame, or press *Shuffle shape* to get a new outline

**Letters**
- Your text repeats around the loop and is spaced so the loop closes evenly
- *Stickiness* overlaps neighbouring letters so they run together
- Random size, tilt, bounce and flip per letter. *Shuffle letters* rerolls them
- Letters can face outward or inward, and can sit on top of the inner shape or tuck under it

**Text effects**
- Case: as typed, UPPER, lower, or a random mix
- Solid, outline, or mixed solid and outline letters
- Stretch, width and slant
- Wave: letter size swells and shrinks along the loop
- Slice: some letters are cut into shifted strips for a glitchy look
- Drift: the letters crawl around the frame as an animation

**Type and color**
- 12 Google Fonts display faces, or load your own `.ttf`, `.otf`, `.woff` or `.woff2` file
- Separate colors for the background, the inside and the letters, with hex input and six preset palettes
- Adjustable print grain

**Image framing**
- Upload a photo to clip it to the frame shape
- Drag to reposition it and zoom to crop
- *Two-tone* maps the photo onto your letter and inside colors for a riso-style duotone

**Output**
- Six one-click presets: Poster, Wave outline, Glitch, Tall & tight, Soft serif and Chaos
- Canvas formats: 4:5, A-size, 1:1, 9:16 and 16:9, all exported at 2000 px on the long side
- Export PNG, or copy the image to the clipboard

## Use it

Open `index.html` in a modern browser (Chrome, Edge, Firefox or Safari). An internet connection is needed for the Google Fonts. Fonts you upload work offline.

To host it, enable **GitHub Pages** for this repository (Settings → Pages → deploy from the `main` branch, root folder). The tool is then live at [kettykuutvuori.github.io/letterloop](https://kettykuutvuori.github.io/letterloop/).

## How it works

Everything is drawn on an HTML `<canvas>`:

1. The frame is a closed Catmull-Rom spline through the control points. *Softness* sets the curve tension.
2. The text is laid out along the spline by arc length. Each letter's width (after overlap) sets how far along the path the next one goes. The number of repeats is chosen so the loop closes evenly.
3. Each letter gets its own transform: it is moved onto the path, rotated to follow the curve, then given random tilt, bounce, flip, stretch and slant. Every random value comes from a seeded hash of the letter's index, so the layout stays the same while you adjust other settings, and only changes when you shuffle.
4. The inner shape is filled, or used as a clipping mask for an uploaded image, and painted above or below the letters depending on *Layering*.

## Credits

Inspired by experimental poster typography and interface patterns from contemporary type tools. Fonts are served by [Google Fonts](https://fonts.google.com) under their respective open licenses.

Made by [KettyKuutvuori](https://github.com/KettyKuutvuori).
