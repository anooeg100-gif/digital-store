# Social Media Design Kit — 6 Editable SVG Templates

Everything in this kit is built for **Harborline Coffee Roasters**, a small-batch
roastery — but every word, color, and shape is meant to be swapped for your own
brand. The sample copy is deliberately specific (real prices, real brew ratios)
so you can see how each layout behaves with believable content.

## Table of contents

| File | Dimensions | Use case |
|---|---|---|
| `templates/post-1080x1350.svg` | 1080 × 1350 px | Instagram portrait feed post — headline, subhead, brand badge |
| `templates/story-1080x1920.svg` | 1080 × 1920 px | Instagram/Facebook story — content kept inside the top 250 px and bottom 320 px safe zones |
| `templates/thumbnail-1280x720.svg` | 1280 × 720 px | YouTube thumbnail — huge bold title plus a circular accent cutout |
| `templates/quote-1080x1080.svg` | 1080 × 1080 px | Square quote card — centered quote with attribution line |
| `templates/banner-1600x900.svg` | 1600 × 900 px | X/Twitter header and Open Graph banner — brand, tagline, CTA |
| `templates/carousel-1080x1350-slide2.svg` | 1080 × 1350 px | Second carousel slide — numbered detail layout, same design system |

Supporting files:

| File | What it is |
|---|---|
| `design-system.md` | Palette, type scale, spacing scale, consistency rules |
| `customize.html` | Dark-UI preview page with live recolor controls |
| `assets/` | Pre-rendered marketing previews of the kit |

## How to edit the SVGs

- **Browser (fastest):** drag an SVG file into a browser tab to see it, then
  view source or open it in any text editor — every heading is a plain
  `<text>` element, and multi-line copy uses `<tspan>` lines you can retype.
- **Figma:** `File → Place image` (or drag the file onto the canvas), then
  ungroup once and double-click any text to edit wording, fonts, and colors.
  Export via `File → Export → PNG` at 1× or 2×.
- **Inkscape:** open the file, double-click text to edit it, and use
  `Edit → Find/Replace` (Search: `fill:#FF5C39`) to recolor across the document.
  Object properties show exact font sizes from the type scale.
- **Canva:** `Uploads → Upload files`, place the SVG on a canvas sized to the
  template's dimensions, then position your own text over it. (Canva treats an
  imported SVG as artwork, so for fully editable text use Figma or Inkscape.)

## How to export PNG

1. **Browser:** open the SVG, use your screenshot tool at the exact window size,
   or run `npx svgexport templates/post-1080x1350.svg out.png 1:1`.
2. **Inkscape:** `File → Export PNG Image`, set the export area to *Drawing* and
   width to the template width (1080, 1280, or 1600 px) — aspect ratio follows.
3. **Figma:** select the frame, Export → PNG, set the export scale to 1×.
4. **Online converters** work too; always confirm the output matches the pixel
   dimensions listed in the table above before scheduling the post.

## Usage terms

- You may use these templates for **your own brand**, for client work, and in
  any personal or commercial project, without attribution.
- **You may not resale, redistribute, or share the source SVG files** — not
  standalone, not modified, and not bundled with another product.
- You may not resell the templates as a template pack, stock asset, or design
  service, or add them to a public template library.
- Edited PNGs and videos exported from the templates are yours to publish freely.

## 5-minute "make it yours" quickstart — change the palette across all 6

The whole kit uses exactly four hex values: `#101828` (Ink), `#F7F5F2` (Paper),
`#FF5C39` (Coral), `#1F7A6D` (Teal).

1. **Pick your two accents** (keep one dark and one light background color):
   e.g. Ink `#1B1B2F`, Paper `#FAF6EF`, Coral → `#E4572E`, Teal → `#2A9D8F`.
2. **Open all six files** in a text editor, or one at a time in Inkscape.
3. **Find and replace each old hex with your new one**, including the `#`
   prefix — this also updates the `<stop>` colors inside the `<linearGradient>`
   blocks, so the gradient shapes follow along automatically. Four replaces ×
   six files, or run replace-all across the whole `templates/` folder.
4. **Check contrast** in `design-system.md`: Ink text on your light background
   and Paper text on your dark background should stay above 7:1; if your new
   accent is very light, put dark text on it instead of white.
5. **Preview:** open `customize.html` in a browser to see all six side by side,
   and use the two color swatch controls at the top to test accent colors live
   before committing them to the files.
6. **Re-export** your PNGs (see above) — you're done.
