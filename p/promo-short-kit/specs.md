# Production Specs — Export, Safe Zones, Upload

Numbers below are for vertical promos exported from CapCut, Premiere, DaVinci, or
Final Cut. Platform limits change; the values are current as of writing — if a
platform rejects an upload, re-check its help page first, then re-encode.

---

## 1. Master export preset (make this once, reuse forever)

| Setting | Value |
|---|---|
| Resolution | **1080 × 1920** (9:16) — export master at this, not 720 |
| Frame rate | **30 fps** constant (60 fps only if you shot motion you want smooth) |
| Codec / container | **H.264 High profile, MP4** (`.mov` also accepted on IG/X) |
| Bitrate | **10–16 Mbps** VBR, 2-pass if your encoder has it (for 30 fps 1080×1920) |
| 60 fps variant | 16–24 Mbps |
| Audio | **AAC-LC, 48 kHz, stereo, 192–320 kbps** |
| Color | Rec.709, progressive (never interlaced), square pixels |
| Loudness | VO ≈ −14 to −16 LUFS integrated, true peak ≤ −1 dBTP |
| File size goal | **Under 100 MB per 15 seconds** — comfortably under every mobile cap |

Everything re-encodes on upload anyway: a clean 10–16 Mbps master survives the
transcode; a crunchy 4 Mbps master turns to mush on the second generation.

---

## 2. Per-platform specs (1080 × 1920 vertical)

| Platform | Exact pixels | Aspect | FPS | Recommended upload bitrate | Duration limits | File limits |
|---|---|---|---|---|---|---|
| **TikTok** | 1080 × 1920 | 9:16 | 23–60 (export 30) | 10–16 Mbps | ~3 s minimum; in-app recording up to 10 min; uploads longer depending on account/region (often up to 60 min) — promos should stay ≤ 60 s | ≈72 MB (Android), ≈287 MB (iOS), ≈1 GB desktop |
| **Instagram Reels** | 1080 × 1920 | 9:16 | 30 (60 accepted) | 10–15 Mbps | In-app recording 90 s–3 min by account; uploads up to 3 min are safe — Reels over 3 min aren't recommended to new audiences; paid boosting works only ≤ 90 s | ≤ 4 GB, MP4/MOV |
| **YouTube Shorts** | 1080 × 1920 | 9:16 (square also qualifies) | 30 or 60 | 10–16 Mbps | **Minimum 15 s, maximum 3 min** (since Oct 2024). Note: Shorts over 1 min with a Content ID music claim can be blocked in some regions — use YT Audio Library tracks | Standard YouTube video upload limits |
| **X (Twitter)** | 1080 × 1920 | 9:16 (also 16:9, 1:1) | 30 or 60 | 5–10 Mbps for ≤60 s; keep under 25 Mbps always | **140 s (2:20) on free accounts**; up to 4 h with Premium | 512 MB free / 16 GB Premium |
| **Facebook Reels** | 1080 × 1920 | 9:16 | 24–60 | 8–12 Mbps | 3 s – 90 s | ≤ 1 GB |
| **LinkedIn** | 1080 × 1920 | 9:16 | 30 | 8–12 Mbps | 3 s min; up to ~10 min mobile / ~15 min desktop | 500 MB |

A 7-second or 15-second promo fits every platform above with zero re-editing —
that's why the kit ships in those two lengths.

---

## 3. Safe zones on a 1080 × 1920 canvas

Platform UI (captions, buttons, handles) floats over your video. Keep **all text and
faces' key features** inside the clear zone. Numbers are practical clearance margins
measured on current app builds; UI shifts with updates, so verify on your own phone.

| Platform | Keep clear: TOP | Keep clear: BOTTOM | Keep clear: RIGHT | Keep clear: LEFT |
|---|---|---|---|---|
| TikTok | 130 px | 500 px | 150 px | 44 px |
| Instagram Reels | 250 px | 420 px | 180 px | 60 px |
| YouTube Shorts | 130 px | 350 px | 160 px | 60 px |
| X | 60 px | 140 px | 120 px | 40 px |

**Universal rule for this kit:** put hook text between **y = 300–720 px**, center text
between **y = 810–1110 px**, never place text above y = 250 px or below **y = 1480 px**,
and keep everything inside **x = 90–990 px**. That clears every platform in the table
without re-cutting.

Other spatial rules:
- **Faces and product detail:** keep eyes/detail above y = 1400 px (above caption zone).
- **Cover frame:** TikTok and Reels crop the cover to 9:16 anyway — design it at 1080×1920.
- **Burned-in captions** (if you add them): center them at y ≈ 1560 px so they clear
  your overlay and the platform's own caption area doesn't stack on top of them.

---

## 4. Duration guidance

| Length | Use it for | Notes |
|---|---|---|
| **7 s** | Pinned profile promo, ad creative, loop post | One idea only: pain → product → proof → CTA |
| **15 s** | Main ad unit, feed post, launch post | Adds the problem beat; still under every boost cap |
| 30–60 s | Cut-down of the 15 s with a real demo added | Only after the 15 s proves it holds attention |

Watch-through is the metric that matters — a 7-second video someone re-watches beats
a 30-second video they abandon at 0:05.

---

## 5. File naming convention

```
<product>_<slug>_<duration>_<version>_<W>x<H>.mp4
```

Examples:
```
ledgerlite_hook-a_v01_1080x1920.mp4
bolddeck_demo_v02_1080x1920.mp4
corkstand_cta-variant-b_v01_1080x1920.mp4
```

Rules:
1. Lowercase, **hyphens between words**, no spaces, no accents — filenames survive
   every platform and cloud drive better that way.
2. `_v01`, `_v02`… on every export you re-do. Never "final", "final2", "final-real".
3. Duration is implied by the slug (`hook` = 7 s, `demo` = 15 s) — or add it:
   `_15s_`.
4. Add today's date in the slug for dated campaigns: `blackfriday_20261015_…`.
5. Cover/thumbnail exported alongside: same base name + `_cover.jpg`.

---

## 6. Pre-upload checklist

**Video**
- [ ] 1080 × 1920, 30 fps, H.264, MP4, file under 100 MB per 15 s
- [ ] First frame contains the hook text — no logo sting, no black frame
- [ ] Last frame is the held end card, not black (loops cleanly)
- [ ] No text above y = 250 px, below y = 1480 px, or past x = 990 px
- [ ] Watched once with **sound off** — every beat still reads from text alone
- [ ] Watched once at 0.5× — no typos, no misaligned pops, no 2-frame flashes

**Audio**
- [ ] VO audible over music (music ducked to −6 dB under speech)
- [ ] No music vocals under the VO
- [ ] Peaks ≤ −1 dBTP, no clipping on the kick drum
- [ ] Ends with a tail, not hard silence

**Content**
- [ ] Every number/claim on screen is *your* real number
- [ ] Exactly one CTA, and it matches where the link actually is
- [ ] Product name spelled correctly in text, VO, and filename

**Upload**
- [ ] Right file, per the naming convention
- [ ] Caption from `captions.md` pasted (one variant, not all three)
- [ ] Cover frame chosen while the video is at 0:00 (or exported `_cover.jpg`)
- [ ] Hashtags: 3–5 relevant, not 30 random
- [ ] Link in bio updated to match this video's CTA before you post
- [ ] Posted to the platform's native upload (not a cross-post watermark with a
      competing app's handle on it)
