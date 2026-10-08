# 8 Text-Overlay Layout Templates

Apply these over your footage in CapCut, DaVinci, Premiere, or your phone editor.
All sizes are **relative to frame height** so they scale correctly to 1080 × 1920 (or
1080 × 1350 if you later crop for a feed post).

**Common rules for all 8:**
- Font: bold condensed sans for headlines (Anton, Archivo Black, Bebas Neue); clean grotesk for body (Inter, Roboto).
- Max 2 lines of body text, max 26 characters per line. Cut words before shrinking type.
- Never place text above **y = 250 px** or below **y = 1480 px** (platform UI will eat it).
- Text must be legible with sound off — if it isn't, it's decoration, not a caption.
- Entrance: 120 ms pop-in (scale 96→100%, opacity 0→100%). Exits are hard cuts with the shot.

---

## 1. Top Third Bold
- **Position:** horizontally centered, block top edge at **y ≈ 300 px** (16% of frame height)
- **Font size:** headline at **7%** of frame height (~134 px cap area, use 72 px type for two lines)
- **Max characters/line:** 26 · **Max lines:** 2
- **Style:** ALL CAPS, white + 6 px black stroke
- **Animation:** pop-in on the first word, second word 120 ms later
- **Best for:** hooks and one-line claims. This is the default layout — use it if you use nothing else.

## 2. Center Smash
- **Position:** dead center, block center at **y ≈ 960 px**
- **Font size:** **8%** of frame height (~150 px) — the biggest type in the pack
- **Max characters/line:** 20 · **Max lines:** 2
- **Style:** white on a solid black box with 12 px padding, or red accent on key words
- **Animation:** scale-in from 90% → 100% in 100 ms with a single shake frame on landing
- **Best for:** the one sentence you want screenshotted. Never use it for more than 4 words a line.

## 3. Lower Third
- **Position:** left-aligned at **x = 90 px**, block bottom edge at **y ≈ 1400 px**
- **Font size:** **3.6%** of frame height (~70 px)
- **Max characters/line:** 34 · **Max lines:** 3
- **Style:** white text on a 70%-opacity black bar, 16 px corner radius
- **Animation:** slides in from the left 24 px over 150 ms, holds, cuts out
- **Best for:** narrated examples, speaker labels, prompt lines — anything that reads like a caption rather than a shout.

## 4. Word-by-Word Karaoke
- **Position:** centered, block at **y ≈ 1150 px** (below center, above caption zone)
- **Font size:** **6%** of frame height (~115 px)
- **Max characters/line:** 22 · **Max lines:** 2
- **Style:** dimmed white base (40% opacity) with the current word at 100% in yellow or brand color
- **Animation:** each word lights up exactly as it's spoken — sync to your VO, not to a beat
- **Best for:** step-by-step sequences and any line longer than 8 words. Keep the whole block visible; never swap lines mid-sentence.

## 5. Number Stack
- **Position:** number at **y ≈ 700 px** (36%), label directly under it at **y ≈ 850 px**
- **Font size:** number at **12%** of frame height (~230 px); label at **3.5%** (~67 px)
- **Max characters/line:** label only, 24 · **Max lines:** 1 label line
- **Style:** number in white or accent color, label ALL CAPS at 80% opacity
- **Animation:** number counts up (or snaps in) over 400 ms; label fades in 200 ms later
- **Best for:** money, stats, countdowns — any script where the figure is the argument.

## 6. Split Header / Footer
- **Position:** header line at **y ≈ 300 px**, footer line at **y ≈ 1380 px**, both centered
- **Font size:** header **5%** (~96 px), footer **3.4%** (~65 px)
- **Max characters/line:** header 22, footer 34 · **Max lines:** header 1, footer 2
- **Style:** header white with stroke, footer in a translucent pill
- **Animation:** header pops in first, footer slides up 16 px 300 ms later
- **Best for:** scenes with strong footage in the middle (demos, b-roll) where the visual needs the center of frame untouched.

## 7. Boxed Keyword
- **Position:** single word or short phrase at **y ≈ 960 px**, offset **x = 90 px** (left-aligned, not centered)
- **Font size:** **6.5%** of frame height (~125 px)
- **Max characters/line:** 14 · **Max lines:** 1
- **Style:** keyword inside a solid accent-color rectangle, black text, slight 2° rotation for handmade energy
- **Animation:** box wipes in left→right over 140 ms (no scale)
- **Best for:** the keyword in a list (RENT. FOOD. GUILT.), monospace prompt lines, tag lines.

## 8. Quote Frame
- **Position:** text block centered between **y = 640 px and y = 1280 px**, quotation marks oversized at the top-left of the block
- **Font size:** **4.5%** of frame height (~86 px), sentence case (NOT all caps)
- **Max characters/line:** 30 · **Max lines:** 4
- **Style:** white serif or light-weight grotesk, thin 1 px rule above and below, 88% opacity
- **Animation:** fade in over 250 ms — the only layout that fades; quotes shouldn't shout
- **Best for:** testimonials, reviews, historical lines, story beats. Hold for at least 1.5 seconds.

---

## Layout selection cheat sheet

| Script beat | Use layout |
|---|---|
| Hook (first 3 s) | 1 Top Third Bold or 2 Center Smash |
| Stats / money / countdowns | 5 Number Stack |
| Spoken example / long line | 3 Lower Third or 4 Karaoke |
| List items / keywords | 7 Boxed Keyword |
| Quote, review, story line | 8 Quote Frame |
| Demo footage that must stay visible | 6 Split Header/Footer |

One layout per beat, one transition per cut. Two competing text styles in the same
second is what makes a faceless video look autogenerated.
