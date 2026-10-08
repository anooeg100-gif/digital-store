# The Micro Tools Playbook

**A practical guide to finding, building, shipping, distributing, and monetizing tiny single-purpose web tools.**

---

## Table of Contents

1. **Chapter 1 — The Economics of Tiny Tools**: What micro tools are, why single-purpose utilities earn, build effort vs. traffic vs. payout, and what monetization actually pays at 100 / 1,000 / 10,000 monthly visits.
2. **Chapter 2 — Finding a Profitable Idea**: Mining autocomplete, "people also ask," Stack Overflow, Reddit, support forums, "X vs Y" queries, and broken existing tools — plus a 20-minute validation ritual with hard pass/fail criteria.
3. **Chapter 3 — Scope Rules That Keep You Shipping**: The one-job rule, the cut list, and the explicit "do NOT build these" list with reasons.
4. **Chapter 4 — Building Fast**: When static HTML+JS with zero backend is enough, the privacy advantage of client-side-only, when you actually need a backend, minimal file structure, a performance budget, and free accessibility wins.
5. **Chapter 5 — Shipping**: Real free-tier hosting limits (GitHub Pages, Cloudflare Pages, Netlify, Vercel), custom domain economics, and on-page SEO for utility pages.
6. **Chapter 6 — Monetization That Doesn't Wreck the UX**: Donations, affiliate, freemium, templates/ebooks, paid API tiers — with concrete price points and realistic conversion rates.
7. **Chapter 7 — Zero-Cost Distribution**: Show HN, Reddit self-promo rules, Product Hunt, dev newsletters, tool directories, answer-marketing that isn't spam, and a launch checklist.
8. **Chapter 8 — Measurement and the Kill/Scale Decision**: The five metrics that matter, lightweight measurement, and a numeric decision rule.
9. **Chapter 9 — Three Fully Worked Examples**: Name, query, scope, stack, hours to build, monetization, and reasoning for each.
10. **Chapter 10 — The One-Page Checklist**: Build → ship → distribute → measure → decide.

---

# Chapter 1 — The Economics of Tiny Tools

## What counts as a micro tool

A micro tool is a web page that does exactly one job for a visitor in under ten seconds. The visitor arrives with a single intent — "convert this JSON to YAML," "count the words in this paragraph," "make this image square" — gets the result, and leaves. There is no account, no onboarding, no dashboard, no newsletter gate. Examples you have almost certainly used: a JSON formatter, a case converter, a base64 encoder, a UUID generator, a regex tester, a markdown-to-HTML box, a color contrast checker, a QR code generator.

The defining property is not size but **single intent**. A tool can be a thousand lines of code and still be a micro tool if it answers one query. A tool can be 80 lines and fail if it tries to be "a developer toolbox" with fourteen tabs.

## Why tiny utilities can earn at all

Three properties of utility traffic make it economically interesting despite its low per-visitor value:

1. **The intent is enormous and evergreen.** "json formatter" alone gets tens of thousands of searches per month worldwide, and the query never goes stale. Nobody stops needing to count words. Unlike a news site or a trend-driven blog, your traffic does not decay to zero when the topic ages out.

2. **The build cost is absurdly low.** A serious version of a case converter is 3–6 hours of work. A JSON formatter with error line numbers is maybe 8–12 hours. The unit you are betting is hours, not months.

3. **The maintenance cost is near zero.** Once it works, it works. There is no content treadmill. The failure mode is not "traffic decayed," it is "you forgot about it."

The economics then reduce to a simple inequality: **(monthly visits × revenue per visit) × your attention must beat what your hours could earn elsewhere.** Everything in this book is about raising the left side of that inequality — more visits, better revenue per visit, less maintenance.

## Build effort vs. traffic vs. payout — the honest math

Payout per visit for utility traffic is small. Let's use real order-of-magnitude numbers rather than optimism:

- **Display ads (programmatic, e.g. via an ad network that accepts small sites):** utility traffic converts terribly because visitors leave in 8 seconds. A realistic range is **$1–$5 per 1,000 pageviews (RPM)** for general utility traffic, with developer-focused audiences occasionally reaching $10–$20 RPM when the ads are for dev products. Many small sites never get approved by the better networks at all.
- **Affiliate (a product genuinely useful to the visitor):** conversion of 0.3–1% of visitors × $20–$80 commission = roughly **$0.06–$0.80 per 1,000 visits**, but highly variable and only works when the tool and the product are topically adjacent.
- **Freemium / paid upgrade:** typically **0.5–2% of regular users** convert if the free tier is genuinely useful and the paid tier solves a real next step. At a $5–$12/month price, 1,000 monthly *returning* users can produce $25–$120 MRR.
- **Sponsorship / donation button:** for a small tool page, expect **$0–$50 per month**, occasionally more if a single appreciative user donates.
- **Selling a related digital product (template, pack, ebook):** a $19 product with 0.5% conversion on 10,000 monthly visits is ~$950/month — but that conversion rate is optimistic; 0.1–0.3% is safer.

So the honest headline: **ads pay least per visit; products and paid tiers pay most; everything in between depends on how well the offer matches the intent.**

## What monetization pays at each traffic tier

### At ~100 monthly visits

Do not monetize. This is your validation window. 100 visits tells you the page ranks for *something* and that people click it. Your only goals: confirm the query, watch where visitors come from, and check whether anyone uses the tool twice (returning-user signal). At this tier, a "Buy me a coffee" link is fine as a courtesy but will earn roughly $0–$3/month. Anything more intrusive (popups, ad slots) will depress the only asset you have — the ability to learn quickly.

### At ~1,000 monthly visits

This is where the first real money appears, and the mix matters.

- **Ads:** $1–$5/month at typical RPMs. Not worth the visual clutter.
- **Donations/sponsors:** $0–$25/month. One appreciative developer can double this in a month.
- **Affiliate for a genuinely adjacent product:** $5–$60/month if the adjacency is real (a regex tester recommending a regex course; an image tool recommending a design asset pack).
- **First digital product:** if you sell a $12 template or pack and 0.2% buy, that's ~$24/month. Plausible but not guaranteed.

The practical conclusion at 1,000 visits: **pick one path, keep it lightweight, and treat the money as a signal rather than income.**

### At ~10,000 monthly visits

Now the numbers change shape:

- **Ads:** $10–$50/month (developer audiences can push this toward $100–$200 if ad density is acceptable). Real, but still the lowest per-visit path.
- **Freemium/paid tier:** at 0.5–1% conversion of *engaged* users, 10,000 visits with, say, 30% returning users gives you 150–300 conversions attempts → realistically **$75–$300 MRR** from a $5–$10 product, growing if the tool compounds.
- **Digital product:** $100–$500/month at 0.1–0.3% conversion on a $19 item.
- **Paid API tier:** if your tool's *function* can be called programmatically (image resize, PDF merge, URL shortening, text analysis), 10,000 human visits often implies thousands of API calls from free-tier users, and 1–3% of those users paying $9–$29/month yields **$50–$300 MRR** — with almost no additional build cost if the core was already client-side.

The crossover lesson: **below ~2,000 visits/month, monetization is a signal; above ~10,000 visits/month, monetization is an income line — but only if you chose a path that pays per intent, not per impression.**

## The real order of monetization paths (per visit, utility traffic)

Rough ranking from lowest to highest revenue per visit for typical single-purpose tools:

1. **Display ads** — $0.001–$0.005 per visit.
2. **Donations button** — $0.000–$0.005 per visit (spiky, reputational, not scalable).
3. **Affiliate** — $0.0005–$0.008 per visit (only with true intent adjacency).
4. **Sponsored mention / flat sponsor slot** — effectively a fixed rent; per-visit value depends entirely on volume.
5. **Freemium/paid tier** — $0.01–$0.15 per visit at healthy conversion, and it compounds with returning users.
6. **Selling your own digital product** — $0.01–$0.05 per visit, fully under your control.
7. **Paid API tier** — highest ceiling, because it monetizes *usage* rather than *eyeballs*.

Ads are included but essentially never the answer for utility traffic: an 8-second visit with 1–2 ad impressions at a $2 RPM pays you **$0.002**. Ten thousand of those visits — a solid month for a small tool — buys you a coffee. Every chapter that follows assumes you are optimizing for paths 5–7.

## The real cost: attention, not code

The hidden cost of micro tools is context-switching, not typing. A portfolio of eight tools that you check weekly, patch twice a year, and monitor with one dashboard is cheap. The same eight tools with a backend, a database, user accounts, and a billing integration is a part-time job. Chapter 3's scope rules and Chapter 4's "static-first" default exist to protect the one resource micro tools are supposed to conserve: **your ongoing attention.**

**Chapter 1 takeaways**

- Micro tools monetize on *intent*, not *impressions*; utility traffic is cheap per visit but evergreen.
- Ads pay $1–$5 RPM — at 10,000 visits/month that is a coffee, not income.
- Paid tiers and your own digital products pay 10–50× more per visit than ads.
- Below ~2,000 visits/month, treat revenue as validation data; above ~10,000, treat it as income.
- The scarce resource is your attention; design the tool so maintenance stays near zero.

---

# Chapter 2 — Finding a Profitable Idea

Ideas are not the bottleneck — *validated* ideas are. Most failed micro tools failed before a line of code was written: the maker assumed a need that either didn't exist, was already served perfectly, or was too rare to route traffic to. This chapter gives you concrete mining sources and a 20-minute ritual with hard pass/fail numbers.

## Where the pain signals actually live

### 1. Google autocomplete and "People also ask"

Autocomplete reflects what real people type *repeatedly*. The technique:

- Open an incognito window, type a seed verb-noun pair and read the completions: `json `, `convert `, `count `, `remove `, `compare `, `check `, `merge `, `split `.
- Append letters to force expansion: `json f...`, `json t...`, `json p...`. Each expansion is a distinct intent.
- Open an actual search result page and collect the **"People also ask"** questions and the **"Related searches"** row. These are Google telling you, in priority order, which adjacent questions it believes are under-served.

Signals of a good query: the completion exists (people search it), the results page is dominated by **ad-heavy aggregator pages, forum threads from 2014, or a single tool with a terrible layout** — not by three polished tools that clearly win.

### 2. Stack Overflow question patterns

Two high-signal patterns:

- **"How do I..." questions with thousands of upvotes and answers that are just code snippets** → the answer exists, but everyone still has to assemble it by hand. A tool that performs that transformation in a browser captures the long tail.
- **"Convert X to Y" / "check if X is valid" questions** repeated across many questions (search `is:question "how do i convert"` and count the duplicates). Duplicate questions are proof of recurring demand — each dupe is a search visit waiting to happen.

Concrete seeds worth checking today: `sql to csv`, `unix timestamp to human`, `cron expression explained`, `diff two texts`, `escape html`, `generate uuid`, `normalize line endings`.

### 3. Reddit and support forums

Search within r/webdev, r/learnprogramming, r/excel, r/dataengineering, r/sysadmin for phrases like *"is there a tool that"*, *"why is there no"*, *"I keep having to"*, *"does anyone know a free"*. The same phrases work in GitHub issue search and in software support forums (Adobe, Notion, Airtable, Shopify communities).

The excel angle deserves special mention: **"excel alternative"** and *"how do I do X in excel"* queries are massive. A browser tool that does one spreadsheet-ish job (split a cell, merge columns, remove duplicates, fuzzy match two lists) captures users who would otherwise fight with formulas — and those users are often professionals with budgets.

### 4. "X vs Y" and comparison queries

`X vs Y` queries (`markdown vs rst`, `csv vs tsv`, `utf-8 vs ascii`, `private vs incognito`) signal a decision moment. A tool can win here differently: not by being the converter, but by being the **interactive comparison** — paste both, see the diff, see the size, see the benchmark. These queries are low-volume individually but have almost no competing tool pages; a cluster of them under one domain compounds well.

### 5. Existing tools with bad UX or broken mobile

This is the fastest signal of all because the demand is already proven — someone already built it and ranks. Your job is to find where they are weak:

- Open the top-ranking tool on a phone. Common failures: textareas too small, buttons below the fold, the page reloads and loses your paste, it requires an account to copy the result, autoplay video ads push the result off-screen.
- Check whether the page **works without JavaScript errors**, whether it handles a 1 MB paste without freezing, and whether it states its privacy posture.
- Check the tool's freshness: copyright year in the footer, dead links, "last updated" dates, unanswered support threads.

If the market leader is slow, ugly, ad-bloated, or mobile-broken, that is your entry: **same job, ten seconds, no nonsense.** You do not need a better idea; you need a better execution of a proven one.

## The 20-minute validation ritual

Set a timer. Answer every gate honestly. Stop immediately on a FAIL — that is the ritual working.

### Minutes 0–5: Demand gate

1. Type the core query into Google. **PASS** if autocomplete offers it (proves repeated searches) *or* the results page shows a "People also ask" box for it.
2. Check at least two keyword sources for a monthly volume number: Google Keyword Planner (free with a Google Ads account), Ahrefs' free keyword generator, or the volume ranges Ubersuggest shows. **PASS** if the head query is ≥ **500 searches/month** OR the sum of a long-tail cluster (e.g. "json to yaml", "yaml to json", "validate yaml") is ≥ **1,000 searches/month**.
3. **FAIL** if the only volume comes from a single brand name (people searching one company's tool) — you'd be renting their trademark.

### Minutes 5–10: Competition gate

4. Look at the top 10 organic results. **PASS** if ≥ 3 are: forum threads, outdated pages (pre-2020 design), ad-choked aggregators, or results that don't fully answer the query.
5. **FAIL** if the top 3 results are all polished, fast, clearly-maintained dedicated tools *and* at least one is a domain with strong authority you cannot out-execute (e.g. a tool built into a major product). Note: a big player ranking with a *generic blog page* still passes — blogs are beatable.
6. Open the leading dedicated tool on your phone. **FAIL** if it is genuinely good on mobile: fast, clean, no interstitials. **PASS** if you find yourself annoyed — your annoyance is a proxy for a million annoyed users.

### Minutes 10–15: Intent gate

7. Write the one sentence the visitor's search represents: *"I have ______ and I need ______ right now."* **PASS** if you can complete it in under 10 words with a concrete artifact (a blob of text, a file, a value).
8. **FAIL** if the intent requires explanation, learning, or configuration ("understand regex", "learn SQL"). Education is a content play, not a tool play.
9. Ask: **does the visitor need to paste data?** If yes, **PASS** with a bonus — paste-intent tools have a natural privacy angle (client-side processing) and a natural freemium line (file size, batch size, history).

### Minutes 15–20: Monetization and moat gate

10. Name one non-ad monetization path from Chapter 6 that fits this intent. **PASS** if you can name one without contorting (an adjacent product to recommend, a "pro" limit worth paying for, an API someone might script against, a related template to sell).
11. Sketch the build in three bullet points. **PASS** if it is ≤ **12 hours** for a solid v1 with mobile support. **FAIL** if v1 needs a database, user accounts, or third-party paid APIs to be useful.

### Scoring

- **11 PASS / 0 FAIL → build this week.** Do not keep shopping; momentum is worth more than a marginally better idea.
- **9–10 PASS, 0 FAIL → build, but keep hunting** for a second idea in the same session; you have a decent-but-not-exciting candidate.
- **Any FAIL → discard in writing.** Add one line to a "graveyard" note: *idea, query, why it failed*. This note becomes your pattern-recognition asset — after ten entries you will spot winners in seconds.

### Extra credit (only if all gates passed)

- Search the query on Reddit and Hacker News. If you find people *currently* complaining about existing tools, screenshot the complaints — they are your feature list and your marketing copy.
- Check if any competitor shows ads on the query page. Advertisers paying for that keyword (look at the ad copy) signal that the traffic is worth money beyond impressions.

**Chapter 2 takeaways**

- Mine autocomplete, People also ask, Stack Overflow duplicates, Reddit phrasing ("is there a tool that…"), and broken mobile experiences of existing tools.
- Run the 20-minute ritual: demand (≥500/mo head or ≥1,000/mo cluster), competition (≥3 beatable results), intent (paste-and-get artifact in 10 seconds), monetization + ≤12h build.
- One FAIL kills the idea; log it in a graveyard note and move on.
- You rarely need a novel idea — you need a faster, cleaner, more private execution of a proven query.

---

# Chapter 3 — Scope Rules That Keep You Shipping

The most common way a micro tool dies is not competition — it's **scope**. The maker sets out to build a word counter and nine weeks later has built "a writing workspace with accounts, sync, and an extension" that has never shipped. This chapter is a set of hard rules to prevent that.

## The one-job rule

**A micro tool answers exactly one query in one sentence.** If your tool's description needs "and" to connect two capabilities, you have two tools.

Test: write the page's `h1` and its meta title. Both must fit the pattern:

> **[Verb] [artifact] [qualifier]** — e.g. "Merge two CSV files, keeping the columns you choose"

If your draft title reads "JSON Formatter **and** Validator **and** Converter," that is three tools wearing a trench coat. Split them (or pick the one with the most search volume and build only that).

Why this discipline pays:

- **SEO**: one page, one query, one clear title = Google knows exactly what to rank you for. Mixed-intent pages rank for nothing.
- **Conversion**: the visitor sees their exact job in the title and stays. Mixed pages create a micro-decision ("which of these do I want?") and micro-decisions create bounces.
- **Maintenance**: one code path, one set of edge cases.

The "and" test applies to features too. A word counter gets: paste → counts. It does not get a grammar checker "while we're at it."

## The cut list (features to cut by default)

Take your feature brainstorm and cut everything in this list unless a specific, evidence-based reason survives the cut:

| Tempting feature | Cut because |
|---|---|
| User accounts / login | Database, password resets, email delivery, support. Months of work, near-zero conversion on a 10-second tool. |
| Cloud save / history | Privacy questions, storage costs, and it *slows down* the first use — the opposite of the value prop. |
| Dark mode toggle as a v1 feature | Nice-to-have; ship OS-preference detection (`prefers-color-scheme`) in 10 lines instead of a settings panel. |
| Settings panel with 15 options | Options are a confession that you didn't decide. Ship one sensible default; add a setting only when users *email* you about it. |
| Accounts to "unlock" the result | Gating the core payoff behind signup destroys trust in a utility. Gate *quantity*, never *the result of a single paste*. |
| Multi-language UI | A translation matrix multiplies every future change. Your analytics will show you 90%+ English for a year. |
| In-app tutorials / modals | If the tool needs a tutorial, the interface failed. The placeholder text in the textarea is the tutorial. |
| Native mobile app | The web page already works on phones. An app store listing for a word counter earns negative dollars per hour. |
| Real-time collaboration | Wrong genre entirely. Requires backend, presence, conflict resolution. |

## Do NOT build these (with reasons)

Some categories are traps regardless of how good your execution is:

1. **Anything gated by a paid third-party API as its core.** If the tool only works because you pay someone per call (OCR, translation at scale, AI summarization), your unit economics are negative from visit one, and a pricing change on their side kills you overnight. (An *optional* paid API integration is different; see Chapter 6.)
2. **A wrapper around one company's product.** "Notion template exporter," "Slack formatter" — one policy change, trademark complaint, or platform API sunset and you're done. Wrappers are fine as *features* of a broader tool, bad as the whole business.
3. **Anything handling sensitive data without a security story.** Password generators are fine (client-side, no storage). "Paste your bank CSV and we'll analyze it on our server" is not — you become a data custodian with real liability and no revenue to fund compliance.
4. **The crowded commodity with zero angle.** Another generic "JSON formatter" can still rank (demand is huge), but only if you bring an angle: faster, better mobile, offline support, batch mode, or a genuinely different UX. If you have no angle and no distribution plan, pick a neighboring query instead.
5. **Tools whose value requires a network effect.** "Share your formatted JSON with a link" needs storage, moderation, and abuse handling. The shared-link feature is a product; the formatter is a tool. Don't accidentally start the product.
6. **"Platforms."** If your idea description contains the word *platform*, *hub*, *suite*, or *dashboard*, it is not a micro tool. Close the notebook.

## The v1 cut-line: a concrete rule

Before writing code, list every capability you can imagine. Then apply:

- **Ship in v1:** everything the visitor needs to complete the single job, plus mobile usability and copy-to-clipboard.
- **Ship in v1.1 (first week of real traffic):** only features requested by actual users, in request order.
- **Never ship without evidence:** everything else.

A working v1 of most text/file utilities is:

```
index.html      — one page: header, one sentence of explanation, the tool, a short FAQ
styles.css      — < 10 KB, mobile-first, dark-mode via media query
app.js          — the transformation logic + copy button + input handling
README.md       — what it does, how to deploy
```

Four files. If your v1 needs a build step, reconsider; if it needs a framework, you are almost certainly wrong for this genre (Chapter 4).

## One deliberate exception: the "cluster" pattern

If your graveyard notes and keyword research show a family of queries — *case converters* (upper, lower, title, camel, snake, kebab) — the one-job rule bends in a specific way: **one page per job, one shared stylesheet, one domain.** The snake_case converter and the kebab-case converter are two pages, not one tool with tabs. Each page gets its own title, its own query, its own shot at ranking — while sharing code, analytics, and monetization. The rule was never "one page per site"; it was **one intent per page.**

**Chapter 3 takeaways**

- One query, one sentence, one `h1`. If the title needs "and," split it.
- Cut accounts, history, settings sprawl, tutorials, and apps from v1 by default.
- Never build: paid-API-dependent cores, single-platform wrappers, data-custody tools without a security story, zero-angle commodities, network-effect features, or "platforms."
- Ship v1 = the job + mobile + copy button. Everything else waits for a real user request.
- Clusters are allowed: one page per intent, sharing code across the site.

---

# Chapter 4 — Building Fast

## The static-first default

For the overwhelming majority of micro tools, **the correct architecture is static HTML + CSS + vanilla JavaScript, no backend, no build step, deployed as files.** The decision tree is short:

- Does the tool transform data the user pastes? → **client-side only.**
- Does it need to generate something (a PDF, an image) the browser can't produce natively? → check again: the browser *can* render to canvas, use WebAssembly, or use `OffscreenCanvas`. Still stuck → a tiny serverless function.
- Does it need to store state across visits? → `localStorage` first; a backend only if the state must sync across devices or users.
- Does it need to authenticate, bill, or rate-limit an API? → serverless function + a hosted auth/billing provider (still no servers you manage).

Roughly 80% of the tools in this book's category never leave the first row.

### The privacy advantage of client-side-only

This is not a technical footnote — it is a **marketing asset you get for free**:

- You can truthfully say *"your data never leaves your browser."* Paste-intent users (developers, accountants, lawyers, journalists) care about this deeply, and no competitor running text through a server can make the same claim honestly.
- You inherit compliance simplicity: no personal data processed or stored means no data-processing agreement, no breach-notification exposure, no cookie banner needed for the tool itself (a consent banner is still required if you add non-essential analytics/ads cookies, depending on jurisdiction — but the tool itself carries none).
- It removes your biggest operational risk: **you cannot leak what you never receive.**

State it plainly on the page: a line like *"Runs entirely in your browser. Nothing you paste is uploaded."* under the textarea. It converts skeptics, and it differentiates you from server-side clones in the results page.

## When you genuinely need a backend

Only four honest reasons:

1. **The computation exceeds the browser** (very large files, minutes-long jobs). Even then, try WebAssembly or chunked processing first — a 50 MB CSV can usually be handled with streaming in the browser.
2. **Rate-limited third-party API calls** — your key must not ship in client JavaScript. Put one serverless function in front; keep everything else static.
3. **Server-generated documents** that the browser can't reliably produce (some PDF layouts, e-mail sending with attachments).
4. **Paid API tier** (Chapter 6) — metering and billing enforcement require a server-side check.

Each serverless function you add is a new failure mode: cold starts, timeouts, deployment config, secrets rotation. Budget **one function maximum** for v1. If you find yourself writing a second, re-read Chapter 3.

## Minimal file structure

```
tool-name/
├── index.html          the entire page
├── styles.css          < 10 KB
├── app.js              < 15 KB unminified for the core transform
├── og-image.png        1200×630 share image
├── sitemap.xml         one URL + lastmod
├── robots.txt          allow all + sitemap reference
└── 404.html            static, links to the tool index
```

Notes that save time later:

- **No framework, no bundler.** A `<script defer src="app.js">` is instant to load, instant to understand, and impossible to break with a dependency update six months from now. If you truly need a component pattern, a 30-line helper that returns an HTML string is enough.
- **Use `<input type="file">` + the File API** for file-based tools and `FileReader` for text — no upload endpoint needed.
- **The textarea is the interface.** Autocomplete off, spellcheck off, `inputmode` appropriate to the content, and `wrap="off"` only for code-like content where line fidelity matters.
- Keep the transformation function **pure and separate** (`transform(input, options) → output`), so you can unit-test it with 10 hand-picked cases in an hour and reuse it if you later add an API tier.

## Performance budget (hit it and the page feels "instant")

Utility visitors are impatient; they arrived mid-task. Treat these as hard limits, not aspirations:

| Metric | Budget | Why / how |
|---|---|---|
| Total page weight (first view) | **< 150 KB** uncompressed is comfortable; **< 300 KB** hard ceiling | No web fonts (use the system font stack), no hero images, no icon libraries — inline SVG icons only |
| Largest Contentful Paint (LCP) | **< 1.5 s** on mid-tier mobile over 4G | Static HTML, no render-blocking CSS/JS, no framework hydration |
| Interaction to Next Paint (INP) | **< 200 ms** | Transform on `input` with a debounce of ~120 ms; never re-render the whole DOM per keystroke |
| Cumulative Layout Shift (CLS) | **< 0.1** (aim 0) | Reserve space for every element; never inject banners above the textarea after load |
| Time to first byte (TTFB) | **< 200 ms** | Static hosting at the edge; this is free with any CDN-backed host |
| JS execution on load | **< 50 ms** | If Chrome's profiler shows more, you're parsing something you didn't need yet |

Concrete tactics that cost nothing:

- Put the `<textarea>` **first in the DOM order after the header** so the tool is usable before anything else finishes.
- Process input **incrementally**: on a 1 MB paste, chunk the work or defer it with `requestIdleCallback`; never block the main thread for > 100 ms — that's exactly when users bounce.
- Serve everything with **`Cache-Control: public, max-age=31536000, immutable`** for hashed assets, and a short cache for `index.html` so you can ship fixes. Static hosts do this for you if you configure headers (Cloudflare Pages and Netlify both support a `_headers`/`_headers`-style config file).
- Test on a real mid-range phone, not your laptop. Chrome DevTools → **Lighthouse** in mobile throttling mode is a 60-second check; run it before you ship, not after a complaint.

## Accessibility basics that cost nothing

These are ~2 hours total and improve the page for everyone:

1. **Real labels.** Every input has an associated `<label for="…">`. Placeholders are not labels — they vanish on focus and fail screen-reader consistency checks.
2. **Keyboard completion.** Everything reachable and operable by keyboard. For the two most important actions (the primary action button and "Copy"), make them real `<button>` elements, not `<div>`s. Native buttons give you Enter/Space activation, focus order, and screen-reader semantics for free.
3. **Focus visibility.** Never `outline: none` without a replacement. A 2 px visible focus ring on inputs and buttons is the entire fix.
4. **Live results.** When output updates as the user types, wrap the output region in `aria-live="polite"` so screen readers announce the change without being spammed (set it to update on debounce, not per keystroke).
5. **Contrast.** 4.5:1 for body text, 3:1 for large text and UI components. The free **WebAIM Contrast Checker** takes seconds; do it once for your palette, dark and light.
6. **Motion.** Respect `prefers-reduced-motion`; a spinner animation is the classic offender.
7. **Errors in text, not just color.** A validation error must say *what* is wrong ("Line 12: expected `,`"), not just turn red.

Bonus payoff: accessible pages rank better and convert better on mobile, and the checklist doubles as your QA script.

## Build-order checklist for the first session

1. Write the static page with realistic sample input pre-filled in the textarea (the sample *is* your demo).
2. Implement `transform()` with 10 test fixtures in comments at the bottom of `app.js`.
3. Wire input → debounce → transform → output + copy button.
4. Mobile pass at 360 px width (the narrowest common phone).
5. Lighthouse run: Performance, Accessibility ≥ 95 on both.
6. Paste 1 MB of real data; confirm no freeze > 100 ms.
7. Only then: meta tags, OG image, sitemap (Chapter 5).

**Chapter 4 takeaways**

- Default architecture: static HTML + CSS + vanilla JS, zero backend; add at most one serverless function, and only for API-key protection, server-side generation, or paid metering.
- Market client-side processing as privacy: *"Nothing you paste is uploaded."*
- Budget: < 300 KB total, LCP < 1.5 s, INP < 200 ms, CLS ≈ 0, JS < 50 ms on load.
- Accessibility is a one-time 2-hour investment: labels, native buttons, focus rings, `aria-live`, 4.5:1 contrast, textual errors.
- Ship order: working transform first, metadata and sitemap last.

---

# Chapter 5 — Shipping

## Free-tier hosting: the real limits

All four major static hosts are free for a tool of this size, but the limits differ in ways that matter for a public utility.

### GitHub Pages
- **Cost:** free; served via Fastly CDN.
- **Limits:** soft bandwidth "soft limit" of ~100 GB/month and a documented recommendation of ≤ 10 GB repositories — enough for any single tool; build limit 10 repo-hours/day (irrelevant if you push pre-built files).
- **Gotchas:** custom domains over HTTPS require a DNS check that occasionally flakes; no arbitrary HTTP headers (no custom `Cache-Control` without workarounds) — mildly annoying for the immutable-assets trick; **no serverless functions** — if you need one, Pages alone won't do it.
- **Best for:** tools that are pure static, versioned in Git, no server logic.

### Cloudflare Pages
- **Cost:** free tier, unlimited bandwidth, unlimited requests.
- **Limits:** 500 build minutes/month, 20,000 files per deployment, 25 MB per file.
- **Extras that matter:** free automatic HTTPS, HTTP/3, and **you can attach a serverless Worker** (Workers free tier: 100,000 requests/day) for the optional API-key-protection function. Also free custom analytics with no cookie banner required for the basic, non-identifying version.
- **Gotchas:** build images are Linux; if you have no build step this is irrelevant.
- **Best for:** the default recommendation for most micro tools — bandwidth freedom plus a path to a Worker later.

### Netlify
- **Cost:** free tier, 100 GB bandwidth/month, 300 build minutes/month.
- **Limits:** 1 concurrent build; forms and functions have their own quotas (125K function invocations/month free).
- **Extras:** excellent CLI (`netlify deploy --prod` gives you a temporary preview URL per deploy — great for screenshotting before launch), `_headers` and `_redirects` config files.
- **Gotchas:** after the free allowance, paid plans start at $19/member/month — budget this in case a launch spike surprises you.
- **Best for:** preview deploys and quick one-command publishing.

### Vercel
- **Cost:** free "Hobby" tier, 100 GB bandwidth/month.
- **Limits:** Hobby plans **cannot be used for purely commercial paid products** under their terms — read before you put a paid API tier there; serverless function timeout on free is short (10–60 s depending on region settings).
- **Extras:** superb preview URLs, edge network, clean analytics add-on.
- **Gotchas:** the commercial-use restriction is the one to take seriously; a donation button is fine, a real paid tier may not be.
- **Best for:** tools where you want preview deploys and might add an edge function.

**Decision rule:** start on **Cloudflare Pages** (unlimited bandwidth + free Worker path). Use GitHub Pages if you want zero third-party accounts beyond GitHub. Move to Vercel/Netlify only if you want their preview workflows — and re-read their terms before monetizing.

## Custom domain economics

A custom domain is the single highest-leverage $10–15/year you will spend: it signals legitimacy in search results, it's brandable in links, and it survives a hosting move.

- **Typical price:** `.com` $10–15/year at Cloudflare Registrar (at-cost pricing, no renewal markup), Namecheap (~$10–12 first year, ~$16 renewal), Porkbun (~$8–11). **Avoid** registrars that sell $1 first years and $35 renewals.
- **Free alternatives:** `*.github.io`, `*.pages.dev` (Cloudflare), `*.netlify.app`, `*.vercel.app` — all free, all HTTPS, but shorter trust and they can't be moved without changing your links.
- **DNS setup:** A/CNAME record → host; wait for propagation (usually < 15 min, occasionally a few hours); enable HTTPS — all four hosts do this automatically via Let's Encrypt with auto-renewal.
- **Watch:** WHOIS privacy is free at Cloudflare/Porkbun/Namecheap — take it; you do not want your home address public. And **turn on registrar lock** the day you buy.

Budget line for a portfolio of 5 tools: 5 domains ≈ $50–75/year, hosting $0, total fixed cost under $100/year.

## On-page SEO for utility pages

Utility SERPs are unusually forgiving: the query is specific, the intent is unambiguous, and Google rewards pages that answer exactly that intent. The entire playbook fits on one page — literally.

### Title patterns that work

The pattern: **`[Primary query]: [specific benefit or qualifier]`**, under ~60 characters.

- `JSON Formatter & Validator — Paste, Format, Find Errors`
- `Word Counter — Paste Text, Get Words, Characters & Reading Time`
- `Case Converter — Convert to snake_case, camelCase & kebab-case`

Rules: put the exact query in the first 40 characters; use a separator (`—`, `|`, `–`); include one differentiator; never stuff synonyms you don't actually support.

### Meta description pattern

140–155 characters, one sentence of what-it-does + one sentence of why-you (privacy, speed, free, no signup):

> *Paste any text to count words, characters, sentences and reading time instantly. Runs in your browser — nothing is uploaded. Free, no signup.*

This is your ad copy in the SERP; write it for the click, not for the algorithm.

### One page, one query

- The `h1` matches (or closely paraphrases) the title's query.
- The first paragraph restates the intent in plain words: *"Paste your JSON below to format it, validate it, and jump straight to any syntax error."* — this is what gets pulled into AI overviews and featured snippets.
- Do **not** build a mega-page covering "JSON tools." Separate pages, separate queries (Chapter 3's cluster pattern).
- **FAQ section: 4–6 real questions** under the tool, each answered in 40–60 words. These win "People also ask" placements and give the page long-tail coverage (`is base64 encryption reversible`, `does word count include spaces`).

### Structured data

Add `FAQPage` JSON-LD for your FAQ block (one `mainEntity` per question/answer pair), plus `WebApplication` or `SoftwareApplication` schema with `applicationCategory: "UtilitiesApplication"`, `operatingSystem: "Any"`, `offers` with `price: 0` (or your price if freemium). Generate it with Google's **Rich Results Test** to validate. FAQ rich results are no longer guaranteed on every SERP, but the markup costs 15 minutes and helps machines understand the page regardless.

### Sitemap and internal linking

- `sitemap.xml`: one `<url>` per tool page with a truthful `<lastmod>`; submit once in Google Search Console.
- `robots.txt`: `Allow: /` + `Sitemap: https://yourdomain.com/sitemap.xml`.
- **Internal linking:** every tool page links to 2–4 sibling tools from a small "Related tools" nav — *Case Converter → Word Counter → Diff Checker*. This spreads link equity across your cluster and gives crawlers the site graph. A tiny hand-written `tools.html` index is a bonus hub page.
- **Search Console:** verify the property the day you ship. It is free, tells you which queries you actually show for, and is the only way to see impressions vs. position for long-tails you didn't plan.

### One thing that beats all of the above

**Backlinks from real mentions.** A tool that gets listed in a "developer tools we love" blog post, a GitHub awesome-list, or a university resources page outranks a perfectly optimized page with no links. Chapter 7 is about manufacturing those mentions.

**Chapter 5 takeaways**

- Host free on Cloudflare Pages (unlimited bandwidth, Worker path); GitHub Pages for pure-static simplicity; read Vercel's commercial-use terms before monetizing there.
- Buy an at-cost domain ($10–15/year), enable WHOIS privacy and registrar lock.
- SEO is one page, one query: query-first title, 155-char benefit description, `h1` match, 4–6 FAQ entries with `FAQPage` + `WebApplication` JSON-LD, sitemap, Search Console, and 2–4 internal links to sibling tools.
- The fastest authority win is being *listed* — pursue real mentions in directories, lists, and posts (Chapter 7).

---

# Chapter 6 — Monetization That Doesn't Wreck the UX

The cardinal rule: **the core job must stay free and instant.** A visitor who came to count words must count words without a modal, an account, or a delay. Monetization attaches to *adjacent* value — more volume, more formats, convenience, or products the visitor already wants. Every path below follows that rule.

## Path 1 — Donations and sponsor buttons

**What it is:** a small "Support this tool" link in the footer, optionally a one-line sponsor slot.

- **Placement:** footer always; optionally a slim static bar *below* the result area (never above the tool). No popups, no interstitials, no exit-intent.
- **Tools:** Buy Me a Coffee (5% + payment fees), Ko-fi (0% platform fee on donations, ~4.35% payment processing), GitHub Sponsors (0% platform cut, but requires a GitHub Sponsors profile approval), Open Collective (for transparency-first projects).
- **Realistic numbers:** median small tool: **$0–$20/month**. One appreciative user occasionally drops $20–$50 at once. At 1,000 visits/month expect near-zero; at 10,000 expect single-digit dollars.
- **When it works:** dev- and pro-audience tools where users understand "free tool = someone's unpaid weekend." Landing pages for marketers donate far less.
- **Sponsor slot variant:** one line — *"Sponsored: [dev tool relevant to your audience] — $40/month flat."* Direct sales via a plain `mailto:` in your footer. One sponsor at $40 is worth more than 20,000 ad impressions. Realistic fill rate: low, but the effort to sell it is 10 emails.
- **Verdict:** keep it on permanently as a courtesy; never count on it as your model.

## Path 2 — Affiliate (only with true intent adjacency)

**What it is:** recommending a product the visitor would plausibly buy *because of the job they just did*, with a tracking link.

Adjacency examples that pass the sniff test:

| Tool | Adjacent offer | Why it fits |
|---|---|---|
| Regex tester | A regex course or ebook (e.g. an Udemy course with 4–8% commission) | The visitor is struggling with regex *right now* |
| CSV/Excel tool | A data-cleaning course, a spreadsheet template pack | Same workflow |
| Markdown editor | A static-site course, a documentation tool's affiliate program | Same job family |
| Color contrast checker | A UI kit, icon set, or design-resource subscription | Same craft |
| JSON/API tool | An API-testing tool (Postman alternatives, Apidog) or a monitoring service | Same workflow |

Bad adjacency (never do this): a word counter recommending a VPN; a base64 encoder pushing web hosting. Generic networks (Amazon Associates at ~1–4% on physical goods) will earn you cents — fine as passive residue, terrible as a strategy.

- **Numbers:** 0.3–1% of visitors click; 5–15% of clickers buy; commission $20–$80 on digital products, so **$0.05–$0.80 per 1,000 visits** when adjacency is real, and it scales with trust.
- **Disclosure:** a one-line "affiliate link" note in the footer or next to the link — required by the FTC and by every network's terms, and it does not reduce clicks meaningfully.
- **Verdict:** one well-chosen affiliate link *in context* (under the tool's output, as a "next step") can out-earn ads by 10× with zero visual cost.

## Path 3 — Genuine freemium

**What it is:** the single job stays free forever; a paid tier removes *volume or convenience* limits.

Limits worth paying to remove (pick the one that matches your tool):

- **File/batch size:** free up to 1 MB or 1 file; Pro handles 50 MB / batch of 100.
- **History:** free = current session (localStorage); Pro = saved presets across devices.
- **Format coverage:** free = the 3 formats 80% need; Pro = the full matrix (30 formats).
- **Scheduled and batch jobs:** free = paste once; Pro = URL input, folders, scheduled re-runs.
- **Usage caps for programmatic access:** free = 20 API calls/day in the browser; Pro = unlimited (this becomes Path 5).

- **Pricing:** utility products convert best at **$4–$9/month** or **$29–$79 one-time lifetime**. Lifetime pricing works well here because your marginal cost is ~zero and users hate subscriptions for tiny tools; a $49 "lifetime" tier often outsells a $6/mo plan at this size. Annual: two months free ($48/yr for a $5/mo plan).
- **Realistic conversion:** 0.5–2% of *engaged* users (define engaged: visited ≥ 3 times in 30 days). Of 1,000 monthly visitors with ~25% returning, expect **2–10 paying users** in a healthy month → $10–$70 MRR from a $9 tier; at 10,000 visits/month, $100–$400 MRR.
- **Checkout without building billing:** Gumroad or Lemon Squeezy (they handle merchant-of-record, VAT, license keys; ~5–10% + fees) — a buy button and an unlock code is a complete v1. Stripe Payment Links (2.9% + 30¢) if you want raw simplicity.
- **Verdict:** the highest-upside path for non-developer-facing tools; only works if the free tier is genuinely excellent — **people pay for tools they already rely on.**

## Path 4 — Selling a related template, pack, or ebook

**What it is:** the tool is free; you sell a digital artifact adjacent to its use case.

Concrete examples: a static-site starter pack sold from a "build a site" tool; a 40-page "SQL cheat sheet" PDF from a SQL formatter; a Figma UI kit from a color/contrast tool; an ebook on regex from a regex tester; a Notion/YAML template pack from a YAML validator.

- **Pricing:** $9–$29 sweet spot for impulse add-ons; bundle 2–3 items at $39–$59.
- **Conversion:** 0.1–0.3% of visitors is realistic; 0.5% if the offer is mentioned *in the workflow* (a line under the output: *"Liked this? The 60-page Regex Field Guide covers the rest."*).
- **Math:** 10,000 visits/month × 0.15% × $19 ≈ **$285/month** — comparable to a freemium tier, with zero support burden (no accounts, no refunds beyond the platform's).
- **Where to sell:** Gumroad, Lemon Squeezy, Paddle — all handle VAT/tax as merchant of record. Delivery is a download link; no fulfillment work.
- **Verdict:** best second monetization layer after the tool itself is proven — you can launch it in a weekend because you already know the audience's pain.

## Path 5 — Paid API tier

**What it is:** expose your tool's function as an HTTP endpoint; free tier for humans, paid tier for scripts.

When it fits: the tool is a *pure function of input → output* (image resize, PDF merge, URL preview, text analysis, QR generation, EXIF stripping), and there exist users who would embed it in a pipeline.

- **Shape:** `POST https://api.yourtool.dev/v1/convert` with a JSON body → JSON response. Free: 20 requests/day, non-commercial, `X-RateLimit` headers. Paid: $9–$29/month for 5,000–50,000 requests, billed via a key.
- **Implementation:** one serverless function (Cloudflare Worker) that validates the key, counts usage in a KV store, then calls your existing transform logic. One weekend if the core is already a pure function — this is Chapter 4's "keep `transform()` pure" paying off.
- **Billing/keys:** Stripe + a simple key table; or use a hosted API-billing layer (e.g. a lightweight gateway) so you don't build metering. Keep it to one function; the metering is the only new code.
- **Conversion:** 1–3% of *developer* users try the API; 5–15% of those trying users pay if the free tier is genuinely rate-limited but usable. At 10,000 human visits/month on a dev-tool page → $50–$300 MRR is a normal outcome.
- **Gotchas:** abuse control (rate limits, payload size caps), a status page, and a written SLA expectation — even "best effort" written down prevents 3 a.m. emails. Re-read your host's ToS (Vercel's Hobby commercial-use restriction again).
- **Verdict:** highest ceiling and the only path that monetizes *usage* rather than visits; start it only after the human-facing tool has real traffic.

## The stacking order (what to add when)

1. **Day 1:** footer donation link + relevant affiliate line (both cost 5 minutes).
2. **~1,000 visits/month:** one sponsor slot offer or the first digital product.
3. **~3,000–5,000 visits/month with returning users:** freemium tier or the full product.
4. **10,000+ visits/month with developer users:** paid API tier.
5. Never: interstitial ads, forced signup for the core result, more than **one** primary monetization element above the fold-adjacent area.

**Measurement note:** each path should be tracked separately (distinct link tags or product IDs) so that after 90 days you can cut the loser without guessing.

**Chapter 6 takeaways**

- Keep the core job free and instant; monetize volume, formats, convenience, or adjacent products.
- Donation buttons earn $0–$50/month; one real affiliate link can earn 10× an ad slot; freemium at $4–$9/mo converts 0.5–2% of engaged users; a $19 product converts 0.1–$0.3%; a paid API tier can reach $100–$300 MRR at 10k visits.
- Use Gumroad/Lemon Squeezy/Stripe Links to avoid building billing.
- Stack monetization in the order: donation+affiliate → sponsor/product → freemium → API, each triggered by traffic thresholds.

---

# Chapter 7 — Zero-Cost Distribution

Distribution is where most micro tools die quietly: a launch gets 200 curious clicks, none convert into backlinks or rankings, and the tool sits. The channels below are ranked by how much they actually move utility traffic — and each comes with the rules that keep you from getting banned.

## Tier 1: channels that move real traffic

### Show HN (Hacker News)

- **Why it works:** a good Show HN posts get 200–2,000 points and, more importantly, **permanent backlinks** from high-authority threads (news.ycombinator.com has enormous domain authority) plus direct traffic from exactly the developer audience that shares tools.
- **How to write the title:** `Show HN: Format JSON in your browser — no upload, no signup`. State the tool, the benefit, one differentiator. Never "I built a platform."
- **Rules of engagement:** post between 8–11 a.m. US Eastern on a weekday; reply to *every* comment within the first 2 hours (HN rewards engagement and punishes drive-by posters); disclose your affiliation plainly if it's not obvious; never ask for upvotes. A "first! 🚀" comment culture doesn't exist here — substance does.
- **Expected outcome:** a good post = 100–800 visits in 48 hours, a handful of backlinks, and (if the tool is genuinely nice) a sticky front page for a few hours. One Show HN on the front page for 4 hours ≈ **1,500–5,000 visits**.
- **Failure mode:** getting flagged for self-promotion. Avoid it by only posting your own tool when it's genuinely novel *and* by having participated in HN comments before.

### Reddit — and its self-promo rules

Reddit is the highest-volume free channel for utility tools, and the most likely to get you permanently banned if you treat it like a billboard.

- **Communities that fit:** r/webdev, r/learnprogramming, r/InternetIsBeautiful, r/coolgithubprojects, r/opensource, r/excel, r/dataengineering, r/sysadmin, r/selfhosted — plus niche subs matching your tool (r/regex, r/typescript, r/macros).
- **The rules that matter:**
  - **Read the sidebar rules before posting.** r/InternetIsBeautiful explicitly bans tools that are "just a simple redirect" and requires you to be transparent; r/webdev's weekly "Showoff Saturday" thread is the only place for self-promotion; many subs require 10:1 participation-to-promotion ratios.
  - **Never post the same link twice** across subs in a short window — Reddit's spam filter treats cross-post bursts as spam.
  - **Lead with the value, not the ownership.** Compliant framing: *"I kept having to convert Unix timestamps by hand, so I made a page that does it in one paste — thought it was useful here."* Non-compliant: *"Check out my new SaaS! 🎉"* with an affiliate link.
  - **Participate first.** An account with 3 months of genuine comments in a sub can post a tool; a day-old account cannot.
- **Expected outcome:** one well-placed post in a mid-size sub (50k+ members): **300–2,000 visits** plus occasional backlinks when someone blogs about it.

### Product Hunt

- **Why it matters here:** PH is weaker for utility traffic than it used to be, but a launch still produces a **dofollow backlink** and a badge you can embed ("Featured on Product Hunt"), which lifts conversion on every other channel.
- **How to launch:** line up 10–20 supporters who will genuinely comment (PH actively flags vote rings); post at 12:01 a.m. PT on a weekday; write a maker comment explaining the *problem*, not the feature list; reply to every comment.
- **Expected outcome:** a top-5 daily finish = 500–3,000 visits; a mid finish = 100–500. Don't optimize for the badge — optimize for the backlink and the screenshots.
- **Reality check:** PH traffic bounces fast; the durable value is authority and the "featured" proof on your landing page.

## Tier 2: slow-burn channels with compounding value

### Tool directories

Submit to every relevant directory — each is a backlink, and several send steady referral traffic for years:

- **Dev-focused:** awesome-python/awesome-javascript PRs (GitHub lists), `github.com/topics` presence, AlternativeTo, Toolfinder, SF.Directory, DevTools enumeration lists, `bashup`-style terminal directories.
- **General:** Product Hunt (also a directory long-term), G2 (free listing), Capterra (free listing), SaaSHub, There's An AI For That (if applicable), plus "awesome" lists on GitHub — many accept well-maintained single-purpose tools.
- **Process:** 10 minutes each, one-line pitch written once, reuse with variations. Do 5 per day for a week → 35 backlinks. **This is the single most boring, highest-ROI hour-per-week you will spend.**

### Dev newsletters

A mention in a newsletter with 10k–100k subscribers can produce **1,000–10,000 visits in a day** — the highest per-effort spike available. Targets with submission forms:

- **This Week in JS / Frontend Focus / CSS Layout News** (frontend tools)
- **Foo Weekly / Codestra / Dev Digest / iOS Dev Weekly** (dev tools)
- **TLDR / TLDR Dev** (tech-brief style; pitch with a one-line hook)
- ** Sidebar, Web Tools Weekly, and the "awesome" newsletter digests**

Pitch template (they receive hundreds; brevity wins):

> Subject: Submission — [Tool]: [one-line job]
> One paragraph: what it does, the privacy/speed angle, why readers care this week. Link. Nothing else.

## Answer-marketing: allowed vs. spam

Answering real questions where your tool is the answer is legitimate and effective **when the answer is the point and the tool is the evidence.**

**Allowed and effective:**
- Stack Overflow: answer a "how do I convert…" question with *working code* and then add, as a secondary line, *"or paste it into this page I built that does it live."* SO allows linking your own tool **when it directly answers the question and you disclose it.** Use `rel="nofollow"` — SO links are nofollow anyway; don't try to game it.
- Reddit comments: reply to someone's actual frustration with a genuinely helpful answer that happens to include your link. One helpful comment in a 500-upvote thread brings **50–500 visits over months** as the thread keeps ranking.
- Quora: same rule — a full, useful answer with the tool as a supplement. Quora links are nofollow but readers click.
- GitHub issues: when someone opens an issue on an unrelated tool asking for a feature your tool does, a polite comment with your link is welcome if it solves their problem.

**Spam (will get you banned and can tank your domain):**
- Posting your link with no accompanying answer ("try this: [link]") — instant removal in most subs and SO.
- Creating multiple accounts to upvote/answer — detected routinely; SO destroys accounts and can nuke the linked domain.
- Bulk-posting the same link across subs/forums in a day.
- Answering with AI-generated walls of text padded with your link — increasingly detected and reported.
- Putting your link in a Stack Overflow question you then answer ("link building" scheme) — explicitly prohibited.

**The litmus test:** if your post would still be useful *even if the link were removed*, it's marketing. If removing the link leaves nothing, it's spam.

## The launch checklist (first 14 days)

**Day 0 (before launch):**
- [ ] Lighthouse ≥ 95 Performance/Accessibility; tested at 360 px width.
- [ ] Meta title/description, OG image, FAQ + `FAQPage` schema, sitemap submitted in Search Console.
- [ ] Donation link + affiliate/sponsor placement live (Chapter 6).
- [ ] Analytics live and verified (Chapter 8).
- [ ] Prepare 3 assets: a 30-second screen recording/GIF, a 1200×630 screenshot, a 40-word pitch.

**Day 1–2:**
- [ ] Submit to 5 tool directories (one per morning).
- [ ] Post Show HN (weekday morning ET).
- [ ] Post to 1–2 Reddit communities *whose rules you've read*, staggered 24 hours apart.
- [ ] Submit to Product Hunt on a weekday.

**Day 3–7:**
- [ ] Send 3–5 newsletter pitches.
- [ ] Answer 3–5 real questions on Stack Overflow/Reddit/Quora where your tool is the evidence, not the point.
- [ ] Open a PR to at least one relevant GitHub "awesome" list.
- [ ] Reply to every comment/issue from the launch; fix anything embarrassing they find.

**Day 8–14:**
- [ ] Check Search Console for impressions; note which unexpected queries appear.
- [ ] Log which channel produced *returning* users, not just raw clicks.
- [ ] Write the "launch retro" line: what to repeat, what to skip.

**Chapter 7 takeaways**

- Tier 1: Show HN (backlinks + dev traffic), Reddit under its rules (transparency, participation ratio, one sub at a time), Product Hunt (authority badge + backlink).
- Tier 2 compounds: 5 directory submissions/day for a week, newsletter pitches with one-line hooks.
- Answer-marketing is allowed only when the answer stands without your link; the link is the evidence, not the content.
- Run the 14-day checklist; measure *returning* users per channel, not raw clicks.

---

# Chapter 8 — Measurement and the Kill/Scale Decision

You cannot improve what you cannot read — and you should be able to read it in **five minutes a week** without a dashboard project. This chapter defines the five numbers, a privacy-light way to collect them, and the numeric rule for whether to kill or scale each tool.

## The five metrics that matter

Every other number is either a vanity metric or a derivative of these five.

1. **Unique visitors per week (U)** — the size of the audience. Tracked per tool, not per site: a portfolio's aggregate number hides which tool is working.
2. **Return rate (R)** — percentage of visitors who come back within 30 days (or, simpler proxy: sessions per visitor). This is the **quality** signal. A tool with 500 visitors and a 30% return rate is a better business than one with 5,000 visitors and a 3% return rate — because returning users convert to paid, share the tool, and survive algorithm changes.
3. **Completion rate (C)** — of visitors who land on the page, what fraction actually *use* the tool (paste or type something, then copy or download the result)? For a micro tool this is your "conversion" and it's measurable with one event: `tool_completed` fired on the copy/download action. Target: **≥ 40%** for a well-matched query; below 20% means either the query doesn't match the tool or the UX loses people mid-task.
4. **Revenue per 1,000 visitors (RPM$)** — total monetization revenue ÷ visitors × 1,000. This is the number that tells you whether your monetization path is working; compare it against the Chapter 1 benchmarks (ads $1–5, affiliate $0.50–8, freemium/product $10–150).
5. **Effort spent this month (E)** — hours of patches, support emails, and fixes. Micro tools live or die on the effort-to-return ratio. Track it honestly in a one-line-per-month log; if E grows while U and RPM$ don't, you have a maintenance trap.

Optional sixth (only if you run a paid tier): **paying users and MRR** — but that's a derivative of RPM$ and you'll see it there.

## Reading them without heavy analytics

Principle: **collect the minimum, keep it on your own domain, and skip anything that requires a cookie banner.**

- **Option A — Cloudflare Web Analytics (free):** a single script tag, no cookies, no personal data, gives pageviews, unique visitors, referrers, and countries. The lightest legitimate option; pair it with…
- **Option B — one custom event:** fire a `tool_completed` event when the visitor copies/downloads the result. With a cookieless, aggregate-only tool (a simple counter endpoint, or Cloudflare's analytics events if available) you get Completion rate without storing anything about the person.
- **Option C — server log lite:** if you host on something with logs, a one-line daily aggregate of requests per path gives you U without any client script at all.
- **Avoid:** full session-replay suites, heatmaps, and tag managers on a utility page — they cost page weight (your Chapter 4 budget), often require consent, and tell you things you'll never act on.

**A weekly five-minute read:**

| Check | Question it answers | Alarm threshold |
|---|---|---|
| U this week vs. last week | Is traffic stable? | < 50% of the 4-week average → investigate rankings/referrals |
| R (return rate) | Do people rely on it? | < 10% → the tool may be a one-off novelty, cut monetization expectations |
| C (completion) | Does the page deliver? | < 20% → fix query-match or UX before marketing more |
| RPM$ | Is monetization viable? | < $1 after 3,000 visitors → change the path (Chapter 6) |
| E (hours this month) | Is it cheap to keep? | > 4 hours/month with flat U → consider archiving |

Log these five numbers in one spreadsheet row per tool per week. Six rows per tool and you can already see trends no dashboard would surface faster.

## The kill/scale decision rule (numeric, 90-day based)

Run this review at **Day 30, Day 60, and Day 90** after launch. Use these inputs:

- **T** = average weekly unique visitors over the last 4 weeks
- **R** = return rate (0–1)
- **C** = completion rate (0–1)
- **$** = revenue per 1,000 visitors in that window

### Scale (double down: add pages in the cluster, add the freemium tier, push distribution)

All three:
- **T ≥ 300/week** (≈ 1,200/month) **and growing ≥ 10% month-over-month** or steady after a launch spike, **AND**
- **C ≥ 0.35** (the query matches and the tool delivers), **AND**
- **R ≥ 0.15** (people come back) *or* **$ ≥ $5** (each visit is already worth something).

→ Action: spend the next month on this tool — cluster expansion (2 sibling pages), one monetization upgrade, one distribution push.

### Hold (keep it, don't invest)

- T between 50 and 300/week, or C ≥ 0.30 but traffic flat, or any tool with E ≈ 0 hours/month.

→ Action: maintenance mode. Monthly log check, zero new features, keep the donation/affiliate line.

### Kill (archive or pivot)

Any one of these after 90 days:
- **T < 50/week** (≈ 200/month) with no growth trend despite having done the Day 1–14 launch checklist, **OR**
- **C < 0.15** after you've already fixed the top UX complaint (traffic arrives but the tool doesn't deliver — usually a query-match failure), **OR**
- **E > 6 hours/month** while T is flat or falling (maintenance trap — the tool costs more attention than it returns), **OR**
- **$ < $0.50 at T ≥ 1,000/month** with no returning-user growth (the monetization path is dead and there's no audience compounding).

→ Action: don't delete it — **archive it.** Put a small banner linking to your better tool, 301 the URL into the cluster if related, or leave it up static (it costs nothing to host). The graveyard entry in your notes records why. Frequently the *right* kill is actually a pivot: keep the traffic, change the monetization, or merge the tool into a sibling page with more volume.

### Why numeric rules beat vibes

The failure mode this prevents is the **"six more months" trap**: you keep patching a tool you emotionally like because it *might* take off, while the one tool that's actually growing gets no attention. A rule you wrote when you were not emotionally invested is the only reliable way to reallocate your limited hours across a portfolio.

**Chapter 8 takeaways**

- Track exactly five numbers weekly: unique visitors, return rate, completion rate, revenue per 1,000 visitors, and hours spent — in one spreadsheet row per tool.
- Use cookieless analytics plus one `tool_completed` event; skip session replay and tag managers.
- At Day 30/60/90, apply the numeric rule: scale at T ≥ 300/wk + C ≥ 0.35 + R ≥ 0.15; hold in the middle; kill at T < 50/wk, C < 0.15, E > 6 hrs/mo, or $ < $0.50 at T ≥ 1,000/mo.
- Killing means archiving, not deleting — host costs nothing; your hours don't.

---

# Chapter 9 — Three Fully Worked Examples

Each example follows the full process: the query, the validation result, the scope, the stack, the build time, the monetization choice, and — most importantly — the reasoning.

---

## Example 1 — "Timestamp Now": Unix timestamp converter

**The query it answers:** *"unix timestamp to date"* / *"convert timestamp to readable date"* — a cluster: `unix timestamp to human readable`, `epoch to date`, `date to unix timestamp`, `timestamp in milliseconds vs seconds`. Combined cluster volume: ~8,000–15,000 searches/month across variants (head query alone is several thousand).

**Why the validation ritual passed (11/11):**
- Autocomplete completes `unix timestamp to ` — demand proven.
- Top 10 results: two Stack Overflow threads (2013-era answers), an ad-choked converter farm, one decent tool buried below ads, and a W3Schools-style page. ≥ 3 beatable results: yes.
- The leading dedicated tool on mobile shows a cookie wall and an interstitial ad before the result — annoyance proxy passed.
- Intent sentence: *"I have a number like 1718000000 and I need the date right now."* — completes in 6 words, paste-a-value intent.
- Non-ad monetization: a paid API tier is plausible (apps do timestamp lookups constantly) and an adjacent product (a developer cheat-sheet) fits.
- Build estimate: 6 hours.

**Scope (one job, with a deliberate sub-variant):**
- Paste or type a timestamp (auto-detect seconds vs. milliseconds) → human date in local time + UTC + ISO 8601.
- Reverse direction: paste a date → get the timestamp. (Justified as *the same job seen from the other side*, the one "and" allowed because users genuinely search both directions and Stack Overflow duplicates prove it.)
- Extras: copy buttons, relative time ("3 hours ago"), and a live "now" ticking value — a 15-line feature that makes the page feel alive.
- **Cut:** no timezone database picker beyond the browser's, no batch mode, no API in v1, no accounts.

**Stack:** single `index.html` + `styles.css` + `app.js`, vanilla JS using `Intl.DateTimeFormat` and `Date`. Zero dependencies, zero backend, no build step. Hosted on Cloudflare Pages. Sample timestamp pre-filled so the page shows an answer before the visitor does anything.

**Hours to build:** ~6 hours total (2 for the transform + edge cases like `0` and negative pre-1970 values, 1 for layout/mobile, 1 for metadata/FAQ/schema, 1 for testing odd inputs, 1 buffer).

**Monetization chosen:** footer donation link + one affiliate line (a developer-cheatsheet/learning product) + a `Cloudflare Worker` API stub **deferred to v2**. No ads.

**Reasoning:** the audience is developers — ads would pay $2–5 RPM to people who run ad blockers anyway. The tool's real asset is returning traffic (devs check timestamps repeatedly), so the plan is to earn trust first, add a free-tier API at ~5,000 visits/month (timestamps are a classic programmatic need), then a $9/mo key tier. The client-side core means `transform()` is already a pure function — the API is a thin wrapper, not a rewrite.

---

## Example 2 — "CleanPaste": remove formatting and hidden characters from pasted text

**The query it answers:** *"remove formatting from text"*, *"strip hidden characters"*, *"clean copy paste from word"*, *"remove zero width characters"*. Cluster: writers, academics, and marketers pasting from Word/Google Docs into CMSs and forms, then fighting with stray `&nbsp;`, smart quotes, zero-width spaces, and invisible Unicode.

**Why the validation ritual passed (10/11, no FAILs):**
- Autocomplete: `remove formatting from ` completes; People also ask shows "how do I paste plain text without formatting."
- Competition: results are mostly forum answers ("Ctrl+Shift+V") and one 2016 blog post; no dedicated, maintained tool ranks. Passed easily.
- Intent sentence: *"I have messy text and I need clean plain text right now."* — artifact = a blob of text. Passed, with the paste bonus.
- Monetization: adjacent product = a writing/SEO workflow template or ebook; freemium possible via batch size.
- Build estimate: 9 hours.
- The one non-pass: head query volume is thin alone (~300/mo) — but the *cluster* (`remove formatting`, `strip characters`, `clean text`, `plain text converter`) sums well over 1,000/mo, which the ritual explicitly allows.

**Scope (one job):**
- Paste rich or dirty text → one button → clean plain text: strips HTML formatting (when pasted as HTML), normalizes smart quotes/dashes, removes zero-width and BOM characters, converts non-breaking spaces, trims trailing whitespace per line, optionally lowercases/unifies.
- A **diagnostics panel**: "found 14 non-breaking spaces, 3 zero-width characters on lines 4, 9, 22" — this is the differentiator. Competitors transform silently; this one *shows what was wrong*, which is what the user actually wanted to know.
- **Cut:** no account, no history, no CMS integration, no batch files in v1 (v1.1 if requested).

**Stack:** static files; character analysis via Unicode property checks in vanilla JS; `beforeinput`/`paste` event handling to capture HTML flavor. Hosted on Cloudflare Pages; Cloudflare Web Analytics + one `tool_completed` event on the copy button. 100% client-side — marketed with the exact line *"Your text never leaves your browser,"* which matters because users paste unpublished drafts, legal text, and client copy.

**Hours to build:** ~9 hours (4 for the character rules + diagnostics, 2 for mobile UX — a textarea-first layout with the button thumb-reachable, 1 for the FAQ/SEO block, 1 for accessibility — `aria-live` on the diagnostics panel, 1 testing with real Word-pasted samples).

**Monetization chosen:** (1) an affiliate link to a writing/grammar product placed *after* the result as a "next step," (2) a $12 "Writer's Workflow Pack" (templates for style guides, editing checklists) sold via Gumroad and linked under the tool, (3) footer donations. No ads.

**Reasoning:** the audience (writers, marketers, academics) is not ad-block-heavy but *is* likely to buy a low-priced workflow product — so a $12 digital product beats an ad slot by orders of magnitude. Freemium was rejected for v1 because there is no natural volume limit (text cleaning is cheap); a paid tier would have to invent an artificial cap, which Chapter 6 warns against. The diagnostics panel also doubles as shareable proof — screenshots of "it found my invisible characters" are exactly what gets posted in writing communities.

---

## Example 3 — "Diff Two Texts": side-by-side text/JSON/code comparison

**The query it answers:** *"diff two texts"*, *"compare two versions of a document"*, *"json diff online"*, *"compare two lists and highlight differences"*. A cluster with dev *and* non-dev audiences (lawyers comparing contract versions, writers comparing drafts, analysts comparing lists).

**Why the validation ritual passed (11/11):**
- Autocomplete and PAA both strong; `json diff online` has solid volume and `compare two lists` has a long tail of spreadsheet-frustrated users.
- Competition: GitHub's diff view is for files/repos (wrong intent), several diff tools exist but are desktop-oriented, ad-heavy, or require account upload. The best-known web diff loads ads above the fold and caps paste size at ~100 KB. Mobile is genuinely broken on two of the top three.
- Intent: *"I have version A and version B and need to see what changed."* Artifact = two blobs. Passed with the paste bonus.
- Monetization: freemium via file size/batch, paid API (CI pipelines diff content programmatically), and an adjacent product (a "code review checklist" ebook).
- Build estimate: 12 hours (the ceiling of the gate — accepted because the diff algorithm is well-documented and I'd use a known approach, not invent one).

**Scope:**
- Two textareas (A and B) → unified or side-by-side diff with line-level highlighting; a "ignore whitespace / ignore case" toggle; JSON mode that diffs by *key path* rather than by line (the real reason devs would choose this over `diff`).
- Copy the diff, download as `.diff`, share via URL (hash-encoded, still client-side — no server storage, keeping the privacy claim intact).
- **Cut (explicitly):** file uploads beyond ~1 MB (deferred), git-style three-way merge (wrong genre), accounts, folders of saved diffs.

**Stack:** static HTML/CSS/JS + a small hand-rolled or vendored diff implementation (a well-known BSD/MIT line-diff algorithm, < 10 KB, kept in-repo so there's no dependency to rot); JSON mode parses both inputs and diffs the resulting key paths. Hash-based share links via `location.hash`. Hosted on Cloudflare Pages; one Worker reserved for a future API tier.

**Hours to build:** ~12 hours (5 for diff core + edge cases — empty input, one-sided additions, CRLF, 500 KB inputs with chunked rendering, 2 for JSON mode, 2 for mobile side-by-side → stacked layout, 1 for SEO/FAQ — `is diff case sensitive`, `how to diff json`, 1 for accessibility — the diff view gets a text summary line for screen readers, 1 buffer).

**Monetization chosen:** freemium is the primary path — free: paste up to 100 KB; Pro at **$5/month or $39 one-time**: 5 MB files, batch of 10 files, saved history in `localStorage`-plus-export, and the JSON key-path mode at full depth. Plus footer donations and a relevant affiliate (a code-quality tool). Paid API tier is v2: `$9/mo` for 5,000 diffs, aimed at CI/CD scripts — server-side metering only.

**Reasoning:** diff is the one example where a *freemium limit is honest* — compute cost and output complexity genuinely scale with input size, so capping at 100 KB doesn't cripple the core job (90% of pastes are tiny) while giving power users a real reason to pay. The one-time $39 lifetime price was chosen over pure subscription because utility buyers dislike subscriptions for intermittent needs; the $5/mo option remains for users who want updates. The JSON mode is the ranking wedge: `json diff online` is a distinct query with weaker competition than generic diff, and one page can win it (cluster pattern from Chapter 3).

---

## What the three examples share

- **Every one is static-first** with client-side processing — privacy claim, near-zero maintenance, free hosting.
- **Every monetization choice follows intent**, not habit: developers get API/donations, writers get a $12 product, power users get honest freemium limits.
- **Build times: 6, 9, and 12 hours** — all inside the 12-hour validation gate. A four-tool portfolio fits comfortably in two weekends.
- **Each has a documented cut list** that was obeyed; each names the v1.1 feature that must wait for a real user request.

**Chapter 9 takeaways**

- Validation gates, scope rules, and monetization matching are the same process applied to three different queries — the query changes, the method doesn't.
- Choose the monetization the *audience* supports: API for devs, product for creators, freemium for power users.
- The differentiator is almost always execution: a diagnostics panel, a mobile layout, a privacy line — not a novel idea.

---

# Chapter 10 — The One-Page Checklist

Print it, pin it, or copy it into your notes. Run it top to bottom for every tool.

## IDEA

- [ ] Query cluster identified: head ≥ 500 searches/month **or** cluster total ≥ 1,000/month.
- [ ] Intent sentence written in ≤ 10 words, ending in a concrete artifact ("I have ___ and need ___ now").
- [ ] Top 10 SERP checked: ≥ 3 beatable results (forums, dated pages, ad-choked or mobile-broken tools).
- [ ] One non-ad monetization path named without contorting.
- [ ] Build estimate ≤ 12 hours; no database, accounts, or paid-API dependency in v1.
- [ ] **20-minute ritual score: ≥ 9 PASS, 0 FAIL** — or the idea is logged in the graveyard with its failure reason.

## BUILD

- [ ] One `h1` / one title / one query — the title passes the "no *and* between two jobs" test.
- [ ] Static HTML + CSS + vanilla JS; ≤ 1 serverless function and only for a named reason (API key, server generation, paid metering).
- [ ] Pure function `transform(input, options) → output`, unit-tested with 10 hand-picked fixtures.
- [ ] Cut list obeyed: no accounts, no history, no settings sprawl, no tutorial modal, no app.
- [ ] Privacy line on the page if client-side: *"Nothing you paste is uploaded."*
- [ ] Sample input pre-filled so the page demonstrates itself.
- [ ] Works at 360 px width; primary buttons real `<button>`s; visible focus rings; labels on every input.
- [ ] `aria-live="polite"` on the output region; errors stated in text, not just color.
- [ ] Lighthouse mobile (throttled): Performance ≥ 95, Accessibility ≥ 95.
- [ ] Budget met: total < 300 KB, LCP < 1.5 s, INP < 200 ms, CLS < 0.1, JS < 50 ms; 1 MB paste does not freeze > 100 ms.

## SHIP

- [ ] Hosted free: Cloudflare Pages (default) or GitHub Pages; headers configured for caching.
- [ ] Custom domain at cost ($10–15/yr), WHOIS privacy on, registrar lock on, HTTPS auto-renewing.
- [ ] Meta title: query first, ≤ 60 chars, one differentiator.
- [ ] Meta description: 140–155 chars = what it does + why you (privacy/speed/free).
- [ ] `h1` matches the query; first paragraph restates the intent in one plain sentence.
- [ ] 4–6 FAQ entries (40–60 words each) with `FAQPage` JSON-LD + `WebApplication`/`SoftwareApplication` schema; validated in Rich Results Test.
- [ ] `sitemap.xml` submitted in Google Search Console; `robots.txt` points to it; 404 page links back.
- [ ] 2–4 internal links to sibling tools; hand-written tools index page.
- [ ] OG image 1200×630; share preview checked.
- [ ] Donation link + at most one in-context affiliate/sponsor placement live.
- [ ] Analytics live: cookieless pageviews + one `tool_completed` event — verified firing before launch.

## DISTRIBUTE (Day 1–14)

- [ ] Day 0: 3 assets ready — 30-second GIF, 1200×630 screenshot, 40-word pitch.
- [ ] Day 1–2: 5 tool-directory submissions; Show HN posted (weekday AM ET); first Reddit post in a sub **whose sidebar rules you read**; Product Hunt submission with lined-up genuine commenters.
- [ ] Day 3–7: 3–5 newsletter pitches (subject line = submission + one-liner); 3–5 real answers on Stack Overflow/Reddit/Quora where the answer stands without your link; PR to one GitHub "awesome" list.
- [ ] Every launch comment replied to within 2 hours; embarrassing bugs found by users fixed same day.
- [ ] Never: same link blasted across subs in a day, no-answer link posts, sockpuppets, or AI-padded replies with your URL.

## MEASURE (weekly, 5 minutes)

- [ ] One spreadsheet row per tool: **U** (unique visitors/wk) · **R** (return rate) · **C** (completion rate) · **$** (revenue per 1,000) · **E** (hours spent this month).
- [ ] Alarms: U < 50% of 4-week avg · R < 10% · C < 20% · $ < 1 at 3,000 visitors · E > 4 hrs/mo.

## DECIDE (Day 30 / 60 / 90)

- [ ] **SCALE** if T ≥ 300/wk (growing ≥ 10% MoM or steady) **and** C ≥ 0.35 **and** (R ≥ 0.15 **or** $ ≥ $5) → next month: cluster expansion + one monetization upgrade + one distribution push.
- [ ] **HOLD** if in between → maintenance mode: monthly check, no new features.
- [ ] **KILL/ARCHIVE** if after 90 days: T < 50/wk with no trend, **or** C < 0.15 after fixing the top complaint, **or** E > 6 hrs/mo with flat traffic, **or** $ < $0.50 at T ≥ 1,000/mo → banner/redirect to a sibling tool, write the graveyard note, reallocate your hours to the tool that passes.

## THE ONLY THREE RULES THAT OVERRIDE EVERYTHING

1. **One page, one query, one job.**
2. **The core job stays free, instant, and (ideally) private.**
3. **Your hours are the budget — when in doubt, cut scope, not quality.**

---

*End of The Micro Tools Playbook.*









