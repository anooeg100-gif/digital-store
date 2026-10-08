# Design System — Harborline Social Media Design Kit

A single system powers all six templates in `templates/`. Every color, size, and
spacing value below is used consistently across the formats, so a post, a story,
and a thumbnail always look like they came from the same brand.

## Palette (4 colors)

| Name | Hex | Where it is used | Contrast note |
|---|---|---|---|
| Ink | `#101828` | Dark backgrounds (story, thumbnail, banner, carousel), all body text on light backgrounds, text on coral badges and buttons | 16.3:1 on Paper — primary text, passes WCAG AAA |
| Paper | `#F7F5F2` | Light backgrounds (post, quote card), all text on dark backgrounds, inner badge discs | 16.3:1 on Ink, 4.8:1 on Teal — always safe for body text |
| Coral | `#FF5C39` | Primary accent: badges, CTA buttons, accent rules, number highlights, gradient endpoints | 5.8:1 with Ink (use Ink text on coral fills); only 2.8:1 with Paper, so never set small Paper text on coral |
| Teal | `#1F7A6D` | Secondary accent: large decorative circles, divider rules, gradient endpoints, attribution lines | 4.8:1 with Paper (passes AA); 3.4:1 with Ink — use only for large shapes or 26 px+ semibold text on dark |

Gradients always run **Teal → Coral** (or Coral → Teal). No other color ever
enters a template, including tints: translucency is expressed with `opacity`,
not with new hex values.

## Type scale

Font stack for every text element (set once on the root `<svg>`):

```
system-ui, -apple-system, "Segoe UI", Roboto, sans-serif
```

| Role | Size | Weight | Line height | Letter spacing | Used for |
|---|---|---|---|---|---|
| Display | 96–120 px | 800 | 1.05× (dy 101–126) | 0 | Story and thumbnail headlines, post headline |
| Title | 80–116 px | 800 | 1.05× | 0 | Banner brand word, carousel slide title |
| Headline | 54 px | 700 | 1.33× (dy 72) | 0 | Quote card body copy |
| Subhead | 30–36 px | 600 | 1.40× (dy 42–44) | 0 | Supporting copy, item values |
| Body | 24–28 px | 400–600 | 1.45× (dy 38) | 0 | Footer lines, helper text |
| Label | 18–22 px | 700 | 1.0× | +2.5 to +5 px, uppercase | Badges, eyebrows, field labels (ORIGIN / ROAST / BREW) |

Rule of thumb: **one Display element per template**, everything else steps down
the scale — never invent an in-between size.

## Spacing scale

Base unit **8 px**. Only these values appear in any layout:

`8 · 16 · 24 · 32 · 48 · 64 · 96`

| Value | Typical use |
|---|---|
| 96 px | Outer margin on 1080 px formats; 120 px on the 1600 px banner; 64 px on the 1280 px thumbnail |
| 64 px | Vertical gap between major blocks (headline → accent rule) |
| 48 px | Gap between a rule and the paragraph under it |
| 42–44 px | Multi-line `dy` step for 30–32 px subheads |
| 32 px | Badge height padding, chip radii |
| 24 px | Footer text size, tight label padding |
| 16 / 8 px | Hairlines, dividers (2 px), micro offsets |

Corner radii follow the same rhythm: small badges `26–28`, chips `32–50`,
buttons `50–56`, large blocks `64` (always half the element height for pills).

Safe zones: Instagram story content stays between **y = 250 and y = 1600**; all
other formats keep content inside their 96 px (or 120/64 px) margins.

## How to keep the 6 formats consistent

1. **Change the palette once, everywhere.** The four hex values above are the
   only colors in the kit. Recolor by find-and-replacing those hex strings in
   all six files (see the README quickstart) — never by editing a single shape.
2. **Keep the font stack on the root.** The stack lives on each `<svg>` element,
   so all `<text>` inherits it automatically. Don't set `font-family` per text.
3. **Reuse the same five components.** Every format is built from the same
   parts: a coral **badge pill** (18 px uppercase label), a **accent rule**
   (160 × 10 px coral or teal), a **Display headline**, a **subhead block**
   (tspans at dy 42–44), and a **footer line** (24 px, brand + lot number).
4. **Respect the margins and safe zones.** Content starts at 96 px (120 px on
   the banner, 64 px on the thumbnail) and nothing critical sits in the story's
   top 250 px or bottom 320 px.
5. **One gradient recipe.** Teal → Coral at 45°, used only for hero shapes and
   top/bottom hairlines — flat fills everywhere else.
