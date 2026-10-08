# Landing Starter

A complete, self-contained landing page template for a small SaaS product. One HTML file, one Markdown file — no build step, no dependencies, no network requests.

**Files**

| File | What it is |
| --- | --- |
| `index.html` | The whole page: semantic HTML5, all CSS in a single `<style>` block, a ~20-line theme toggle script. |
| `README.md` | This file. |

**What's on the page**, in order: sticky top nav (wraps on mobile — no hamburger, no JavaScript required for navigation), hero with value proposition and primary/secondary CTAs, social-proof logo strip, six-card features grid, three-step "How it works", a three-tier pricing table with the middle tier highlighted, three testimonials, a five-item FAQ built on native `<details>`/`<summary>`, a final CTA band, and a footer with four link columns.

The sample content is a plausible product ("Harbor — client portals for independent studios") so you can read the copy as a real example and replace it section by section.

---

## Change these 10 things first

1. **Product name and logo mark** — the string `Harbor` and the `<span class="brand-mark">H</span>` square appear in the header, the hero mock URL and the footer.
2. **Hero headline** — the single `<h1>` in `#hero`. Keep it to one line of meaning; the supporting sentence is `.lead` right below it.
3. **CTA hrefs** — every `href="#pricing"` / `href="#cta"` is an in-page anchor standing in for your real signup and demo URLs. Replace them with your signup, trial and contact links (the `mailto:` address in the FAQ intro too).
4. **Palette variables** — the `:root { … }` block at the top of the `<style>` tag (and the two dark-theme blocks that mirror it). Change `--accent`, `--accent-hover`, `--accent-contrast` and `--accent-soft` together; they drive buttons, links, badges, focus rings and the CTA band.
5. **Feature cards** — six `<article class="card">` blocks in `#features`: swap the `<h3>`, the paragraph, and the inline SVG icon inside `.ic-box`.
6. **Pricing numbers and features** — the three `<tr>` rows in `#pricing`: `.plan-name`, `.plan-for`, `.plan-price`, and the `<li>` items in `.ticks`. The highlighted row is the one with `class="featured"`.
7. **Testimonial names and quotes** — three `<figure class="quote">` blocks: the `<p>` quote, the `<b>` name, the `.role` line, and the two-letter `.avatar` initials.
8. **FAQ items** — each `<details>` in `#faq`: a `<summary>` question and a `<p>` answer. Add or remove whole `<details>` blocks freely; nothing else needs to change.
9. **Footer links** — the four `<nav class="footer-col">` columns and the `.fineprint` row. Placeholder links are `href="#"`; point them at real pages.
10. **Meta title and description** — the `<title>` and `<meta name="description">` in `<head>` are what search results show. Update `<meta name="theme-color">` to match your accent.

---

## Where the colors live

All colors are CSS custom properties declared in the `:root { … }` block at the very top of the `<style>` element — nothing in the rest of the stylesheet hard-codes a color. Three declarations of the same variable names handle theming:

```css
:root { …light tokens… }                                  /* default */
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) { …dark tokens… }       /* follows the OS */
}
:root[data-theme="dark"] { …dark tokens… }                /* manual override */
```

The `<script>` before `</head>` reads `localStorage.theme`, writes `data-theme` on `<html>` before first paint (so there is no flash of the wrong theme), and wires up the "Dark mode / Light mode" button in the nav. With JavaScript off the page still works — it just follows the OS setting and hides the button.

Keep the light and dark blocks in sync: when you add a token (say `--success`), add it to **both** dark blocks as well.

## Adding a new section

1. Copy an existing `<section id="…" class="section">` block inside `<main>` and place it where you want it.
2. Give it a unique `id` and add a matching `<a href="#…">` to the nav `<ul class="nav-links">` (and the footer "Product" column, if it matters).
3. Reuse the built-in pieces: `.section-head` with `.eyebrow` + `.h2` + `.lead` for the intro, `.cards`/`.card` for grids, `.quote` for quotes, `.band` for a tinted background, `.btn .btn-primary`/`.btn-secondary` for buttons.
4. Use `<h2>` for the section title and `<h3>` inside cards — the page ships with exactly one `<h1>` and a consistent hierarchy.

New components only need `var(--…)` tokens, a `rem`-based size, and `minmax(min(100%, …), 1fr)` grids so they collapse cleanly on narrow screens.

## Browser support

Evergreen Chrome, Edge, Firefox and Safari (roughly the last two years). The page relies only on flexbox, CSS Grid, custom properties, `clamp()`, `prefers-color-scheme`, `prefers-reduced-motion`, `:focus-visible` and native `<details>` — all widely supported since 2020–21. There is no legacy fallback for Internet Explorer; browsers without `clamp()` still get a readable page at the fallback values. Tested layout range: 360 px phones up to wide desktop, with no horizontal scrolling.

## Why no framework and no external requests

- **Zero network cost.** No web fonts, CDN, analytics or framework bundle means the page renders from a single file, works offline, and is trivially cacheable. Nothing can break because a third party changed a URL.
- **No supply chain.** No dependencies to audit, pin or patch; nothing to update for a security advisory.
- **Easy to reason about.** The whole page is one readable document: change a value in the `:root` block and the result is visible immediately, with no build output to inspect.
- **Portable.** Drop `index.html` on any static host — object storage, a repo, a USB stick — and it just works. Add a framework later only when the page actually needs interactivity beyond the theme toggle.
