# Portfolio v2 — Design System

The single reference for every visual decision on the v2 site. Values come from what is already built (Figma → `v2/index.html`).
Every value here exists as a CSS custom property in the `:root` block of `v2/index.html` — use the token, never a raw value. Items marked **[applied]** were drift fixes from the first audit; new open questions go in §10 with an **[open]** tag until decided.

---

## 1. Personality

- **Physical and playful.** Things can be grabbed, peeled, pulled and flicked (notch, stickers, pull-cord). Motion is springy, never floaty.
- **Editorial type.** Tall condensed display headlines, monospace for everything you *read*.
- **One blue, warm paper.** A single brand blue on a cool white frame; content sits on warm cream "paper" cards.
- **Quiet chrome, loud moments.** The frame, nav and text stay calm so the interactive pieces carry the delight.

---

## 2. Color

### Brand blue (one hue, a few steps)
| Token | Value | Used for |
|---|---|---|
| `--blue-900` | `#2D38B8` | Hero gradient top |
| `--blue-600` | `#006CFA` | **The** accent: links, CTA text, focus rings, card-title gradient start, "My Work" gradient start |
| `--blue-500` | `#0F80FA` | Hero gradient middle |
| `--blue-300` | `#61A5FF` | Card-title gradient end (decorative only) |
| `--blue-100` | `#CCEAFF` | CTA button gradient end |
| `--blue-50`  | `#F6FAFF` | "My Work" gradient end |

**[applied]** Retire `#007AFF` (testimonial pill) → use `--blue-600`. They are two different blues 1 step apart.

### Ink (text)
| Token | Value | Used for | Contrast |
|---|---|---|---|
| `--ink-strong` | `#212121` | Names, emphasised words | ≥ 15:1 |
| `--ink` | `#363636` | Section headings | ≥ 11:1 |
| `--ink-muted` | `#646464` | Kickers, descriptions, meta | 5.7:1 on paper ✓ |
| `--ink-subtle` | `#767676` **[applied]** | Secondary body (About bio) — replaces `#979797` (2.9:1, fails) | 4.5:1 ✓ |
| `--ink-on-blue` | `#FFFFFF` | Text on the hero gradient | — |

Body copy is never pure `#000`. **[applied]** testimonial quotes `#000` → `--ink-strong`.

### Surfaces
| Token | Value | Used for |
|---|---|---|
| `--surface` | `#FFFFFF` | Page, frame, popover |
| `--paper` | `#FEFAEF` | Case-study & testimonial cards |
| `--paper-shade` | `#E9E4D6` | Empty media / image placeholders |
| `--line` | `#EBEBEB` | Borders, dividers (**[applied]** merge `#E8E8E8` into it) |

### Gradients
| Token | Value |
|---|---|
| `--grad-hero` | `#2D38B8 0% → #006CFA 75% → #4C97FB 84% → #B3D3FD 93% → #FFFFFF 100%` — blue holds to 75% so white hero copy always passes 4.5:1, then eases into white |
| `--grad-display` | `linear-gradient(to bottom, #006CFA, #F6FAFF)` — "My Work" |
| `--grad-title` | `linear-gradient(to bottom, #006CFA, #61A5FF)` — card titles |
| `--grad-cta` | `linear-gradient(to bottom, #FFFFFF, #CCEAFF)` |

### Texture
| Token | Value | Used for |
|---|---|---|
| `--grain` | SVG fractal-noise tile, 220px, 16% opacity, `overlay` blend | Hero gradient (under the copy) |

**Rules:** one accent hue only; no new blues outside this scale; text that must be read uses an ink token, never a light blue.

---

## 3. Typography

### Families
| Role | Family | Weights |
|---|---|---|
| Display & titles | **Paralucent Condensed** | 500, 600, 700 |
| Reading text, meta, kickers | **Geist Mono** | 400, 500, 600 |
| Small UI (tooltips) | Paralucent | 500 |

Three families maximum. No serif, no fourth face.

### Scale (desktop → phone)
| Token | Size | Family / weight | Line height | Tracking | Example |
|---|---|---|---|---|---|
| `display-xl` | 120 → 40 | Condensed 700 | 1.0 | -4% | Hero headline |
| `display-l` | 150 → 56 (fluid) | Condensed 700, UPPERCASE | 1.2 | -4% | "My Work" |
| `heading-l` | 80 → 48 | Condensed 700, UPPERCASE, `--grad-display` | 1.0 | -4% | "Kind words" |
| `heading-m` | 48 → 28 | Condensed 600 | 1.0 | -2% | Case-study title |
| `heading-s` | 24–31 | Condensed 700 | 1.2 | -4% | About card title |
| `title` | 20 | Condensed 600 | 1.2 | -2% | Testimonial name |
| `label` | 20 / 16 | Condensed 600 or Mono 500, UPPERCASE | 1.2 | -4% | Pill, kicker |
| `body-l` | 18 → 15 | Mono 400 | 1.5 | -4% | Hero subline |
| `body` | 16 | Mono 400 | 1.5 | -4% | Testimonial quotes |
| `body-s` | 14 → 13 | Mono 500 | 1.4 | -4% | Card description, About bio |
| `caption` | 13–14 | Condensed 500 | 1.2 | -2% | Roles, tooltips |

**Rules**
- Headings use `text-wrap: balance`; paragraphs `text-wrap: pretty` **[applied]**.
- Reading text max ~65ch.
- Sentence case for headings (proper nouns and "I" capitalised). UPPERCASE only for: hero CTA, "My Work", labels/kickers.
- Mono text uses -4% tracking at every size, including long paragraphs (decided — see §10).

---

## 4. Spacing

4px base. Use only these steps: `4 · 8 · 12 · 16 · 24 · 32 · 48 · 64 · 80 · 120`.

| Token | Value |
|---|---|
| `--section-y` | 80 desktop · 64 tablet (≤1024) · 48 phone (≤640) |
| `--gutter` (frame inset) | 16 · 8 phone |
| `--page-x` (content side padding) | 24 |
| Card inner padding | 12 |
| Stack gap inside cards | 12 |

**[applied]** snap stragglers: hero sub `21 → 24`, hero CTA `37 → 32`, card gap `10 → 12`, tooltip `6×11 → 8×12`.

---

## 5. Radius

| Token | Value | Used for |
|---|---|---|
| `--r-xs` | 4 | Media inside a card |
| `--r-sm` | 8 | Case-study card, avatar top-left notch |
| `--r-md` | 12 | Frame, CTA, glass pill, avatar |
| `--r-lg` | 18 | Testimonial card |
| `--r-xl` | 24 (×scale) | About popover |
| `--r-full` | 50% | Stickers, knob |
| `--r-pill` | 999px | Segmented toggle and its thumb |

Rule: inner radius = outer radius − padding (tighter inside, softer outside).

---

## 6. Elevation (shadows)

**[applied]** tint every shadow navy (`rgb(13 30 80)`) instead of black, and use one light source (from above).

| Token | Value | Used for |
|---|---|---|
| `--shadow-1` | `0 1px 3px rgb(13 30 80 / .06), 0 6px 20px rgb(13 30 80 / .06)` | Frame, cards at rest |
| `--shadow-2` | `0 2px 6px rgb(13 30 80 / .10)` | Raised UI (CTA, pill) |
| `--shadow-hover` | `0 6px 20px rgb(13 30 80 / .18)` | Hovered raised UI |
| `--shadow-3` | `0 24px 60px rgb(10 30 90 / .28), 0 2px 8px rgb(0 0 0 / .08)` | Popover |
| `--shadow-lift` | `0 22px 18px rgb(13 30 80 / .28)` | Things being dragged |
| `--text-shadow` | `0 4px 8px rgb(0 0 0 / .15)` | Display text |

---

## 7. Motion

| Token | Value | Used for |
|---|---|---|
| `--ease-spring` | `cubic-bezier(.34, 1.56, .64, 1)` | Hover pops, sticks, tooltips |
| `--ease-out` | `cubic-bezier(.22, 1, .36, 1)` | Entrances, returns |
| `--ease-in` | `cubic-bezier(.5, 0, .75, 0)` | Exits (popover retract) |
| `--dur-fast` | 150ms | Fades |
| `--dur-base` | 300–350ms | Hover, press |
| `--dur-slow` | 600–800ms | Entrances, fly-backs |

Rules: animate only `transform`, `opacity`, `filter`, `clip-path`. Every animation has a `prefers-reduced-motion` fallback. Physical things (notch, cord, stickers) use simulated springs; everything else uses the tokens above.

---

## 8. Layering (z-index)

| Layer | Value |
|---|---|
| Content | 0–5 |
| Notch nav | 10 **[applied]** (currently 2) |
| Pull-cord | 40 |
| Popover (About) | 50 |
| Dragged sticker | 100 **[applied]** (currently 1000) |

---

## 9. Components (current inventory)

- **Frame** — fixed rounded window, all content scrolls inside it.
- **Notch nav** — liquid-glass, draggable, returns after 5s, tooltips.
- **Section heading** — 1–3 words, Condensed 700, UPPERCASE, `--grad-display` text fill (`display-l` for pinned stages, `heading-l` elsewhere), followed by a mono `body-l` subline in `--ink-muted`. Never a full sentence in the fading gradient.
- **"Currently" pill** — light liquid-glass pill pinned top-left of the hero (joins the flow, centred above the headline, below 1080px): pulsing green live dot, what I'm doing, and my local time (Asia/Kolkata, "IST"; adds "probably asleep" before 7 AM). Optional "On repeat" song with animated equaliser bars. Content lives in the `CURRENTLY` object in the script (edited by hand; YouTube Music has no public now-playing feed).
- **Work-experience tags** — a paper tag per company in the lower hero, in date order (AthrVEd → ForeignAdmits → BigBlockTheory), each hanging from its own glossy blue pushpin (pins in a row at 20 / 50 / 80% of the width; no connecting line — tried and rejected). Tag: round logo (blue Condensed monogram until a real logo exists), company in Condensed 600, years in mono, green dot on the current one; dark tooltip with role and exact dates on hover, or tap on touch. Each tag is a damped pendulum about its pin: swings in on load, the cursor's movement stirs a breeze, tags can be grabbed and flicked. Runs only while moving and on screen; static under reduced motion.
- **Hero CTA** — white→blue-100 gradient, Condensed 700 uppercase, blue-600 text.
- **Glass pill** — section label.
- **Work toggle** — liquid-glass segmented control (Design Work / AI Work), centred at the bottom of the pinned Work stage (the deck reserves room for it). The thumb is liquid glass with the notch's layer recipe (softer `#thumb-glass` distortion, blur, white tint, rim, shine) and acts as a lens above the labels, showing a 1.12× magnified blue copy of the text beneath; a spring drives its position and width, it stretches and squashes with speed, swells to 1.1× while held, and can be dragged — it snaps to the nearest tab on release. ARIA tablist; ← → switch; switching restarts the deck on the new set.
- **Case-study card** — paper, notched image mask, mono kicker/year, gradient title, mono description, peelable sticker.
- **Sticker** — WebGL-rendered round sticker (white disc + logo). Hover: the edge nearest the cursor lifts slightly and the sticker leans toward it with a holographic sheen. Grab: a flap curls over a cylinder from the grabbed edge to show the paper backing, the sticker lifts (shadow grows) and tilts with drag speed. Drop anywhere to stick; returns home after 5s. Springs drive every value; flat CSS fallback without WebGL.
- **Work, option B (gallery frame)** — *live; option A (card deck, `#work`) is temporarily shown above it and will be removed later.* Pinned stage: a still gold frame (`assets/gold-frame.png`, opening insets 18.52 / 15.9 / 16.96 / 15.9 %) beside a project list. Scrolling drops the next picture in from the top *inside* the opening while the current one sinks back (scale 0.92, brightness 0.7). The active project unfolds glass tags, a 54px gradient title and description; the rest stay as faded 36px titles that scroll to their project on click.
- **Tools desk** (`#tools`) — laid out like the Work stage: a giant centred "MY TOOLS" (`--title` size, `--grad-display`) with the MacBook overlapping its lower part (desk `margin-top: -0.62 × --title`) and the mono hint underneath. The iPhone is parked (`hidden`). The desk box takes the laptop's outline from the camera angle (`--desk-ar`, set by the 3D script; 1.19 for the CSS Mac fallback) and is capped at 1000px / 76svh tall. The 3D canvas bleeds 25% past the desk so the shadow and drag never hit its edge; the section clips sideways overflow. The camera is fitted to the open laptop's measured box and view-offset to centre it. Six tool keycaps (Figma, Claude, ChatGPT, Gemini, Framer, Adobe) use the supplied logo images in `assets/tools/*.png` (256px; ChatGPT's black mark is drawn white on keys). Pressing a key (click, tap or 1–6 while in view) plays a Web Audio "thock" and springs an app window onto the screen whose mono description types out (instant under reduced motion; announced via a polite live region). **3D Mac:** when WebGL is available, a three.js render of `assets/models/macbook.glb` (Sketchfab model by jackbaeten, CC BY 4.0, credited in the Credits dialog; compressed with gltf-transform meshopt + WebP, 10.6MB → 1.2MB) sits exactly over the CSS Mac, which stays invisible underneath so its buttons still work for keyboard and screen readers (a focused button lights its 3D key). Camera is square-on and high (~53°) so the keyboard reads from above while the screen still faces the viewer. It loads 1200px before the section, the lid springs open on first view, the screen is a live canvas drawing the same app window, tool keycaps with brand-colour backlights sit on keys 1–6 (full-pitch invisible tap targets), hover tilts it slightly and dragging turns it, springing back on release. Renders only while on screen; the CSS Mac returns if loading fails.
- **Testimonial card** — paper, avatar + name/role header, dashed divider, mono quote.
- **About popover** — slides from behind the notch.
- **Pull-cord** — doorbell.
- **Footer** — "Say hello" mono label, email in Condensed 600 with a Copy button (status announced politely), mono uppercase links with ↗, base line (© · "Built with Claude Code" · back to top), then a giant "AVISH" wordmark in the section-heading treatment, sized to the frame's inner width and cropped by its bottom edge.
- **Credits dialog** — "Credits" text button in the footer base line opens a native modal `<dialog>` on paper (gradient Condensed title, ✕ button, dashed-divider list of item + mono attribution with blue links). Closes on ✕, Esc or a click outside; springs in, plain under reduced motion. Add every third-party asset here.
- **Name card** — dictionary entry on paper (word, part of speech, numbered senses with emoji, mono definition). Trails the cursor on hover, opens on tap or keyboard focus, closes on leave, Esc, outside tap or scroll.

---

## 10. Decisions log

- Mono tracking stays **-4%** everywhere, including long paragraphs.
- Hero subline contrast fixed by holding the hero blue to 75% (4.8:1 at 1280×695, 5.4:1 at 1440×900, 6.6:1 on phones).
- One section-heading style: the **"My Work"** treatment (see Components).
- Hero gets a subtle film grain (`--grain`) to move it away from a flat "AI gradient".

## 11. Pre-ship checklist

- [ ] Colors only from §2, text contrast ≥ 4.5:1 (≥ 3:1 for text ≥ 24px)
- [ ] Font sizes only from §3, headings balanced
- [ ] Spacing only from §4
- [ ] Radius/shadow/motion/z-index from tokens
- [ ] Every interactive element: hover, press, focus-visible
- [ ] Reduced-motion fallback for every animation
- [ ] Real content (no placeholders), alt text on meaningful images
- [ ] Meta description + OG tags, skip link
