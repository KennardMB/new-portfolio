# Kean — Portfolio site brief + AI prompt

*Written 2026-09-05. Use this to brief a designer or paste **Part B** into Cursor / v0 / Claude to generate the site.*

**Person:** Kennard Mahib Bariumanto (“Kean”)
**Site job:** Personal brand. One thesis — *PM who codes* — with work, scholarships, and freelance as lanes, not three different identities.
**Visual:** macOS Dark Mode as a **website**, with a **macOS window chrome** as the single signature (desktop only).
**Primary CTA:** Get in touch. **Secondary:** CV.

---

## How to use this file

1. Read Part A if you need to change IA, copy, or tokens.
2. Paste **Part B** as the entire prompt to the builder. It is self-contained.
3. Do not let the builder invent a new palette, a light mode, Inter/Geist, or a fake Mac desktop (dock, wallpaper, menu bar).

**Sources for the design system**

- Apple Human Interface Guidelines — Color: https://developer.apple.com/design/human-interface-guidelines/color
- Apple HIG — Dark Mode: https://developer.apple.com/design/human-interface-guidelines/dark-mode
- Apple HIG — Materials / Liquid Glass: https://developer.apple.com/design/human-interface-guidelines/materials
- Measured dark-mode sRGB values (Apple does **not** publish guaranteed hex; these are reference measurements, mainly [iccir’s NSColor dump](https://gist.github.com/iccir/b2601d4c9b1ae3a31651b3a25124f9e8) and [Sonoma 14.4 catalog samples](https://gist.github.com/martinhoeller/38509f37d42814526a9aecbb24928f46)). Design to **semantic roles**, not to chasing pixels across OS versions.

---

# Part A — Brief

## 1. Positioning

**Name on the site:** Kean
**Legal / about name:** Kennard Mahib Bariumanto
**One-line thesis:** Product manager who codes. I used to write the PRD. Now I ship the build.

**Who it has to work for (in this order)**

1. Hiring managers and builders deciding if he can actually ship (Cara / Robbin / Povvy).
2. Scholarship committees scanning for trajectory, writing, and proof (IELTS 8.5, IISMA, ITS, ADA).
3. Freelance clients who need to know he can scope and deliver a web/iOS thing.

One homepage. No “I wear many hats.” No separate /pm vs /dev vs /scholar sites.

**Voice:** Direct, warm, peer-to-peer. Short sentences. Technical is fine. No “crafting digital experiences,” no “passionate about,” no emoji, no dummy Latin.

**Primary action:** Email `kennard.mahib@gmail.com`
**Secondary:** LinkedIn `https://linkedin.com/in/kennardmahib` and a CV download (PDF).
**Do not publish** the phone number on the public site.

**Location line:** Jakarta-born. Based in Kuta, Bali. Apple Developer Academy, Bali (Mar 2026–present).

## 2. Visual direction (locked)

**Hybrid, as approved**

- The *system* is Apple’s macOS dark semantic UI: window gray, not OLED black; SF Pro; hairline separators; `systemBlue` as the only accent; Liquid Glass on chrome and the primary button only.
- The *signature* is a macOS window around the page on desktop: traffic lights, toolbar with the current page title, optional sidebar. **Not** a Finder parody. No dock, no desktop wallpaper, no Apple menu, no fake menu bar spanning the viewport.

**Dark only.** No light-mode toggle. Provide dark + increased-contrast token comments in CSS so Liquid Glass still has a pair, but do not ship a light theme.

**What this should feel like:** Opening Notes / System Settings on a dim MacBook — raised gray window, vibrant blue on one control, everything else quiet. Not apple.com marketing. Not a Dribbble “OS UI kit.”

**The one risk:** the window chrome. Spend the boldness there. Everything inside the window is disciplined HIG.

## 3. Color tokens (macOS dark, reference)

Map every color to a CSS custom property named after the **semantic role**. Use the hex/rgba as the dark-mode implementation for the web.

### Surfaces (back → front)

| Token | Role | Dark reference | Use |
|---|---|---|---|
| `--under-page` | underPageBackgroundColor | `#282828` | Viewport behind the window (desktop “desk”) |
| `--window` | windowBackgroundColor | `#323232` | Window chrome, toolbar, sidebar |
| `--content` | textBackgroundColor / controlBackgroundColor | `#1E1E1E` | Main content area inside the window |
| `--grouped` | elevated grouped surface | `#2C2C2E` | Cards, inset grouped lists |
| `--grouped-2` | tertiary grouped | `#3A3A3C` | Nested cells, hover wells |
| `--unemphasized-sel` | unemphasizedSelectedContentBackground | `#464646` | Inactive selection / pressed row |

Do **not** use pure `#000000` as the page background. macOS dark windows sit on a mid-dark gray, not an OLED void.

### Foreground

| Token | Role | Dark reference | Use |
|---|---|---|---|
| `--label` | labelColor | `rgba(255,255,255,0.85)` | Primary text, names, headlines |
| `--text` | textColor | `#FFFFFF` | Long-form body if you need full white; prefer `--label` for UI |
| `--secondary` | secondaryLabelColor | `rgba(255,255,255,0.55)` | Subheads, meta, captions |
| `--tertiary` | tertiaryLabelColor | `rgba(255,255,255,0.25)` | Disabled, section eyebrows, timestamps |
| `--quaternary` | quaternaryLabelColor | `rgba(255,255,255,0.10)` | Hairlines, placeholders of last resort |
| `--placeholder` | placeholderTextColor | `rgba(255,255,255,0.50)` | Form placeholders |
| `--separator` | separatorColor | `rgba(255,255,255,0.10)` | 1px rules, sidebar borders, toolbar bottom |

### Accent and system colors

Use **one** accent for interactivity: dark `systemBlue`. Links may use `linkColor` (slightly lighter). Do not rainbow the UI. System colors other than blue are for **status / project tags only** (tiny pills), never for backgrounds.

| Token | Role | Dark reference | Use |
|---|---|---|---|
| `--accent` | systemBlueColor | `#0A84FF` | Primary button fill, key window selection, focus ring |
| `--link` | linkColor | `#419CFF` | Inline text links |
| `--accent-light` | controlAccent (blue, aqua measurement) | `#007AFF` | Avoid for dark fills; `#0A84FF` is the dark system blue |
| `--red` | systemRedColor | `#FF453A` | Close traffic light; destructive only |
| `--orange` | systemOrangeColor | `#FF9F0A` | Minimize traffic light analog `#FEBC2E` is the real window button |
| `--yellow` | systemYellowColor | `#FFD60A` | Tag only |
| `--green` | systemGreenColor | `#32D74B` | Zoom traffic light analog `#28C840`; success tags |
| `--pink` | systemPinkColor | `#FF375F` | Tag only |
| `--purple` | systemPurpleColor (macOS measured) | `#6260E0` | Tag only |
| `--gray` | systemGrayColor | `#98989D` | Neutral tags, SF-style glyphs |

**Traffic lights (standard macOS window controls, not HIG system colors):**

- Close `#FF5F57`
- Minimize `#FEBC2E`
- Zoom `#28C840`
- Idle (unhovered): desaturated versions of the same, ~70% opacity, no icons until hover
- On hover: show `× − +` glyphs in a dark 60% opacity, 8–9px

**Focus ring:** 3px `--accent` at ~50% alpha, 3px offset. Keyboard users must see it.

**Do not:** gradients, glow, colored section backgrounds, glass tinted in brand colors, purple/black “AI portfolio” palettes.

## 4. Type

**License constraint:** San Francisco is not a free webfont. Do **not** download, self-host, or hotlink SF Pro files.

```css
--font-ui: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display",
  "Helvetica Neue", system-ui, "Segoe UI", sans-serif;
--font-mono: "SF Mono", ui-monospace, "Menlo", "Monaco", monospace;
```

On Apple devices this *is* SF. Everywhere else it falls back cleanly. That is correct.

**Scale** (Apple default Dynamic Type at 100%, then a larger display step for the hero only):

| Role | Size / line | Weight | Tracking |
|---|---|---|---|
| Hero display | 48–56 / 1.05 | 590–600 | -0.02em |
| Large Title | 34 / 41 | 400 or 700 | -0.01em |
| Title 1 | 28 / 34 | 400 | -0.01em |
| Title 2 | 22 / 28 | 400 | 0 |
| Title 3 | 20 / 25 | 400 | 0 |
| Headline | 17 / 22 | 600 | 0 |
| Body | 17 / 22 | 400 | 0 |
| Callout | 16 / 21 | 400 | 0 |
| Subheadline | 15 / 20 | 400 | 0 |
| Footnote | 13 / 18 | 400 | 0 |
| Caption 1 | 12 / 16 | 400 | +0.01em |
| Caption 2 | 11 / 13 | 400 | +0.02em |
| Eyebrow | 11–12 / 16 | 400 | +0.12em, uppercase, `--secondary` or `--tertiary` |

Body copy uses `--label` or `--secondary`, never gray-on-gray. Headlines use `--label`. Meta uses `--secondary`. Do not set body in a serif.

**Icons:** SF Symbols language — small, monochrome, `--secondary`. Export a tiny set as inline SVG (thin/regular weight, rounded). Do not use Lucide, Heroicons, Feather, or emoji as UI icons.

Suggested set: `envelope`, `arrow.up.right`, `chevron.right`, `safari`/`link`, `person`, `square.and.arrow.down` (CV).

## 5. Chrome, materials, motion

**Desktop (≥900px)**

```
[ under-page #282828, padding 24–40 ]
  ┌─ window, radius 10–12, 1px separator border, subtle shadow ─────────┐
  │ ● ● ●     toolbar title (current page)              [Get in touch]  │
  │─────────────────────────────────────────────────────────────────────│
  │ sidebar 220px │ content #1E1E1E                                      │
  │  About        │                                                      │
  │  Work     ←   │   page                                               │
  │  Contact      │                                                      │
  └───────────────┴──────────────────────────────────────────────────────┘
```

- Window max-width ~1120–1280px, centered, min-height ~calc(100vh − 48px).
- Toolbar height 52px. Traffic lights 12px, 8px gap, 20px left inset, vertically centered. They are decorative (do not close the site). Title is the page name, 13px, `--label`, optically centered in the toolbar.
- Sidebar: `--window` fill, 1px `--separator` on the right. Rows 32–36px, 8px radius, selected row uses `--accent` at 18–24% fill + white label, or `--grouped-2` with `--label`. Source List energy, not a website nav with huge padding.
- Primary CTA in the toolbar: Liquid Glass **tinted** with `--accent` (the only tinted glass control). Label “Get in touch”.

**Mobile (<900px)**

- Drop the window, the traffic lights, and the sidebar.
- Viewport is `--content` (`#1E1E1E`) or `--window`; not the under-page gray as a full-bleed gimmick.
- Sticky top bar: glass, wordmark “Kean”, Get in touch.
- Hamburger or bottom segment: About / Work / Contact.

**Liquid Glass (web translation)**

- `backdrop-filter: saturate(180%) blur(20px);`
- Fill: `rgba(50,50,50,0.72)` for chrome; `rgba(10,132,255,0.82)` for the primary button only.
- 1px top highlight `rgba(255,255,255,0.18)`, 1px border `rgba(255,255,255,0.10)`.
- Do not frost every card. Cards are opaque `--grouped`.

**Radius:** 10px window, 8px controls/rows, 6px pills. Not 999 “pill everything,” except tags and the primary button (999).

**Shadows:** one window shadow (`0 24px 80px rgba(0,0,0,0.45)`). No card drop shadows. Separation is color + hairline.

**Motion:** 200–280ms, `cubic-bezier(0.22, 1, 0.36, 1)`. Sidebar active state, row hover, page fade ~8px. Respect `prefers-reduced-motion: reduce`. No scroll-jacking, no marquee, no particle fields, no looping gradient.

## 6. Information architecture

| URL | Title in toolbar | Job |
|---|---|---|
| `/` | Kean | Thesis, selected work, proof, contact |
| `/work/cara` | Cara | iOS case study |
| `/work/robbin` | Robbin | AR game case study |
| `/work/povvy` | Povvy | Web case study |
| `/about` | About | Bio, path, scholarships, how he works |

No blog required. No /services page. Freelance is a short block on Home + a sentence on About, not a sales funnel.

**Home sections (in order)**

1. Hero — name, thesis, one supporting sentence, two buttons (Get in touch, CV).
2. Selected work — three rows/cards: Cara, Robbin, Povvy. Each: name, one-line, stack chips, → case study.
3. Proof strip — 4–6 facts as a grouped inset list (not a colorful stat grid).
4. Path — compact timeline: Vidio → Tiket → Garena → ADA.
5. Contact — email, LinkedIn, one line on freelance.

**Case study template (all three)**

1. Eyebrow (platform + year)
2. Title + one-sentence pitch
3. Role / team / stack (footnote list)
4. Problem
5. User (who it is for)
6. What shipped (bullets, not features dump)
7. One decision that shows PM+code judgment
8. Outcome or honest status (if no public metric, say so — do not invent)
9. Next (what’s open)

## 7. Copy (use this; do not rewrite into marketing)

### Home — hero

**Eyebrow:** Apple Developer Academy · Bali

**Display:** Kean

**Title:** PM who codes.

**Body:** Three years shipping product at Garena, Tiket, and Vidio. Now I build the thing myself — Swift, React, Godot — at the Apple Developer Academy in Bali.

**Buttons:** Get in touch · Download CV

### Home — selected work

**Cara** — Post-stroke home care, for the family member doing the work. iOS, SwiftUI, SwiftData.
**Robbin** — Real archery in your real room. ARKit + Vision, endless survival.
**Povvy** — Video-message keepsakes for celebrations. Guests record at the event; the family keeps them. `povvy.id`

### Home — proof (exact facts)

- IELTS 8.5
- Garena, Free Fire Indonesia — weekly QA 3 days → 1 day (−70%); ~65% fewer human errors on the asset pipeline
- Tiket.com — +3% CTR on homepage/campaigns; Rp 7.8B transaction value via landing pages
- ITS Information Systems — GPA 3.83/4.00
- IISMA — Monash University exchange, High Distinction
- Apple Developer Academy Bali — Mar 2026–present

### Home — path

- **Vidio** — Product Management Intern, 2021–22
- **Tiket.com** — Product Management Intern, 2024
- **Garena** — Product Associate, Game Operation, Free Fire Indonesia, 2024–26
- **Apple Developer Academy** — iOS, Bali, 2026–present

### Home — contact

Email kennard.mahib@gmail.com. LinkedIn /in/kennardmahib. Available for freelance web and iOS work; also happy to talk scholarships, product, or builds.

### About (body)

Kennard Mahib Bariumanto. People call me Kean. I grew up in Jakarta and live in Kuta, Bali.

I spent about three years as a product manager — internships at Vidio and Tiket.com, then Product Associate on Free Fire Indonesia at Garena. The through-line was the same: talk to users, write the spec, ship with engineering, measure. At Garena that meant Notion ops + bots for asset publishing, FGDs and data work on new-user experience, a newbie AI-tips bot, and anti-cheat monitoring for the Indonesian community.

In March 2026 I joined the Apple Developer Academy in Bali to close the loop: I still think in PRDs and acceptance criteria, but the default stack is now Swift / SwiftUI / SwiftData, plus React and Godot when the problem is web or a game.

I’m applying for fully-funded international master’s programs (IELTS 8.5 in hand). I take freelance work — web, iOS, voiceover, proposals — when it’s a clear scope.

How I work: concrete output over advice. Technical is fine. Direct, no padding. Push back if the idea is weak.

### Cara case study

**Pitch:** Cara is an iOS app for the **caregiver**, not the patient. Post-stroke home care is a pile of easy-to-get-wrong tasks taught once at discharge. Cara turns that into a daily checklist with plain-language steps and inline safety rules.

**User:** Spouse or adult child, no clinical background, now doing morning/afternoon/night care.

**Shipped:** Daily routines; per-day checklist; Learn library across 7 clinical categories; vitals (BP, HR, SpO₂, temp); daily notes; date navigation; seeded real task content so it works on first launch.

**Stack:** SwiftUI, SwiftData, MVVM, iOS 26+, Liquid Glass, GitHub Actions CI. Team project (CH3-PM-Team4). AGPL-3.0.

**Decision:** The user is the caregiver. That choice drives large targets, short sentences, and safety rules in the step itself (“if systolic BP < 100, hold the med and call the nurse”) — not a buried PDF.

**Status:** Academy project; local persistence, no backend. Do not invent App Store rankings or user counts.

### Robbin case study

**Pitch:** Real-world archery. Point the phone to aim (ARKit, rear camera). Draw an invisible bowstring in front of your face (Vision, front camera). Survive an escalating horde in your actual room.

**Team:** aileen, brent, lilo, gusti, kean.

**Loop:** spawn → aim → draw → release → hit/miss → score. Endless survival, Subway Surfer / Fruit Ninja pacing, Time Crisis in the DNA.

**Shipped / in-build:** gesture state machine Idle → Draw → Release; Archer’s Sigil; charge meter; pause (manual + on background); countdown; Game Center leaderboards; Wanted Poster share sheet; TelemetryDeck; haptics; spatial audio. Enemies: Crow (tempo) and Falcon (punishes slow full draws). Scoring: base × combo (up to ×5).

**Stack:** iOS, ARKit, Vision, SwiftUI HUD.

**Decision:** Draw distance/speed maps to power — snap shots vs full draws is a bodily risk/reward, not a button.

**Status:** GDD still open on reference art and a second arrow type. Do not invent download numbers.

### Povvy case study

**Pitch:** Memories, kept warm. Guests leave video messages at a celebration via QR. The family gets a keepsake.

**Shipped:** One guest-recording app, deployed **per event via config, not forked**. Landing at povvy.id. Upload Worker to R2 with rate limit + Turnstile.

**Stack:** Monorepo on Cloudflare — `@povvy/brand`, Next.js 16 landing (static → Pages), Vite event app, Worker. Brand: illustrated stationery (paper `#F8F3E9`, ink `#2B2823`, sealing-wax `#C2352B`).

**Decision:** Events are content + theme + `VITE_EVENT_ID`, so a wedding does not mean a new codebase.

**Status:** Open — redraw hero doodles to the final logo hand, finish Povvy Hand glyphs, wire email capture to a Pages Function + D1. Do not invent customer counts.

## 8. Components (build these, not a generic kit)

- `WindowShell` — desktop chrome; identity collapse on mobile
- `Toolbar` — lights, title, glass CTA
- `SourceList` — sidebar
- `GroupedList` — inset grouped table (proof, path, contact)
- `WorkRow` — 72–96px row: title, one line, chips, chevron; hairline separators
- `Chip` — 11px, `--grouped-2` fill, `--secondary` text
- `PageHeader` — eyebrow + title + dek
- `CaseSection` — 13px eyebrow + body
- `Footer` — footnote inside the window: © Kean, Bali, year

## 9. Stack and quality bar

- Next.js (App Router) on Vercel, static-friendly. System fonts only. No UI kit (no shadcn-looking defaults, no Tailwind palette of slate-950 + indigo-500). Tailwind is fine if tokens above are the only colors.
- Responsive, keyboardable, `:focus-visible` rings, `prefers-reduced-motion`.
- Contrast: `--label` on `--content` must hold ~AAA for body; `--secondary` only for secondary text. Check `--accent` button label is white.
- Real favicon: simple “K” in SF, `--label` on `--window`.
- CV: link a PDF path `/kennard-mahib-cv.pdf` and flag if the file is missing — do not fake a download.
- Placeholder imagery: if no screenshots yet, use labeled `--grouped` rectangles (`Cara · Home`, 9:19 phone; `Povvy · landing`, 16:9). No stock photos, no Unsplash faces, no generated “founder in a turtleneck.”

## 10. Do not

- Inter, Geist, Space Grotesk, Recoleta, or any “AI startup” pairing
- Light mode, theme toggle, or OLED `#000` full-bleed
- Fake Mac desktop (wallpaper, Dock, menu bar, Spotlight)
- Traffic lights that navigate or close tabs
- Numbered 01 / 02 / 03 markers unless they are a real sequence
- Lorem ipsum; invented metrics, clients, or App Store ranks
- Phone number on the page
- Purple gradients, blob backgrounds, grain overlays, custom cursors
- Embedding SF Pro font files

---

# Part B — Copy-paste AI prompt

```
Build a production-quality personal portfolio website for Kennard Mahib Bariumanto (goes by Kean). Dark-only. It must look like a macOS Dark Mode app window in the browser — Apple HIG semantic color and type — NOT apple.com marketing, NOT a fake desktop OS (no dock, no wallpaper, no menu bar), NOT a generic AI portfolio (no Inter/Geist, no OLED black + acid green, no purple gradients).

## Who this is
Jakarta-born, based in Kuta, Bali. “PM who codes”: ~3 years product (Vidio intern, Tiket.com intern, Garena Product Associate on Free Fire Indonesia) now paired with hands-on iOS/web/game builds at the Apple Developer Academy Bali (Mar 2026–present). Freelance on the side. Applying for fully-funded master’s programs (IELTS 8.5).

Thesis (do not paraphrase into marketing): “PM who codes. I used to write the PRD. Now I ship the build.”
Voice: direct, warm, peer-to-peer, short sentences, technical is fine. No “passionate about,” no “crafting experiences,” no emoji.

Primary CTA: mailto:kennard.mahib@gmail.com (“Get in touch”).
Secondary: LinkedIn https://linkedin.com/in/kennardmahib and Download CV (file at /kennard-mahib-cv.pdf; if missing, still render the control).
Do NOT show a phone number.

## Visual system (locked)

SIGNATURE (desktop ≥900px): the site lives inside a centered macOS window on an under-page background.
- Viewport / “desk”: #282828 (underPageBackgroundColor)
- Window: #323232, 10–12px corner radius, 1px rgba(255,255,255,0.10) border, shadow 0 24px 80px rgba(0,0,0,0.45). Max width 1120–1280px, centered, vertical margin ~24–40px.
- Toolbar 52px: traffic lights (12px, 8px gap, 20px left inset) Close #FF5F57, Minimize #FEBC2E, Zoom #28C840. Decorative only. Idle = slightly desaturated; hover shows × − + in dark 60%. Toolbar title = current page name, 13px, optically centered. Right side: primary “Get in touch” button.
- Optional left Source List sidebar 220px: About, Work, Contact. Selected row like macOS sidebar (accent wash or #3A3A3C). 1px separator on the right.
- Content well: #1E1E1E (controlBackgroundColor / textBackgroundColor).

SIGNATURE (mobile <900px): DROP window, lights, and sidebar. Sticky glass top bar with “Kean” + Get in touch. Normal scrolling dark site. Do not keep fake traffic lights on a phone.

MATERIALS: Liquid Glass ONLY on toolbar/sidebar chrome and the primary button.
- backdrop-filter: saturate(180%) blur(20px)
- chrome fill rgba(50,50,50,0.72); primary button fill rgba(10,132,255,0.82)
- 1px top highlight rgba(255,255,255,0.18)
Cards and lists are OPAQUE #2C2C2E. Do not glass everything.

COLOR TOKENS (semantic names; hex is measured macOS dark reference — Apple does not guarantee hex across OS versions; do not invent a new palette):
--under-page: #282828
--window: #323232
--content: #1E1E1E
--grouped: #2C2C2E
--grouped-2: #3A3A3C
--label: rgba(255,255,255,0.85)
--secondary: rgba(255,255,255,0.55)
--tertiary: rgba(255,255,255,0.25)
--quaternary: rgba(255,255,255,0.10)
--separator: rgba(255,255,255,0.10)
--accent: #0A84FF   /* systemBlue dark */
--link: #419CFF      /* linkColor dark */
--red: #FF453A
--green: #32D74B
--orange: #FF9F0A
--gray: #98989D

Use --accent on ONE primary control and on the selected sidebar row. Inline links use --link. Other system colors are tiny tags only. No section-colored backgrounds. No gradients.

TYPE: Do NOT self-host SF Pro (license). Use:
font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", "SF Pro Display", "Helvetica Neue", system-ui, sans-serif;
Mono: "SF Mono", ui-monospace, Menlo, Monaco, monospace.
Scale: hero 48–56px weight 590; Large Title 34; Title 2 22; Body 17/22; Footnote 13; Caption 11–12 uppercase +0.12em tracking for eyebrows.
Icons: inline SVG in SF Symbols language (thin, monochrome). No Lucide/Heroicons/emoji UI.

RADIUS: window 10–12, rows 8, pills 999 for chips + primary button only.
MOTION: 200–280ms cubic-bezier(0.22, 1, 0.36, 1). Respect prefers-reduced-motion. No scroll-jacking.

## Pages
/ home
/about
/work/cara
/work/robbin
/work/povvy

Stack: Next.js App Router, deployable to Vercel. System fonts only. Tailwind allowed ONLY if these tokens are the colors. Accessible: focus-visible ring 3px #0A84FF at 50%, keyboard nav, semantic HTML.

### Home copy (use verbatim)
Eyebrow: Apple Developer Academy · Bali
Display: Kean
Title: PM who codes.
Body: Three years shipping product at Garena, Tiket, and Vidio. Now I build the thing myself — Swift, React, Godot — at the Apple Developer Academy in Bali.
Buttons: Get in touch · Download CV

Selected work (each links to its case study):
- Cara — Post-stroke home care, for the family member doing the work. iOS, SwiftUI, SwiftData.
- Robbin — Real archery in your real room. ARKit + Vision, endless survival.
- Povvy — Video-message keepsakes for celebrations. Guests record at the event; the family keeps them. povvy.id

Proof as a macOS inset grouped list, not a colorful stat grid:
- IELTS 8.5
- Garena, Free Fire Indonesia — weekly QA 3 days → 1 day (−70%); ~65% fewer human errors on the asset pipeline
- Tiket.com — +3% CTR on homepage/campaigns; Rp 7.8B via landing pages
- ITS Information Systems — GPA 3.83/4.00
- IISMA — Monash University exchange, High Distinction
- Apple Developer Academy Bali — Mar 2026–present

Path: Vidio intern 2021–22 → Tiket.com intern 2024 → Garena Product Associate 2024–26 → Apple Developer Academy 2026–present.

Contact: Email kennard.mahib@gmail.com. LinkedIn /in/kennardmahib. Available for freelance web and iOS work; also happy to talk scholarships, product, or builds.

### About copy (use verbatim sense; you may break into paragraphs)
Kennard Mahib Bariumanto. People call me Kean. I grew up in Jakarta and live in Kuta, Bali.
I spent about three years as a product manager — internships at Vidio and Tiket.com, then Product Associate on Free Fire Indonesia at Garena. The through-line: talk to users, write the spec, ship with engineering, measure. At Garena: Notion ops + bots for asset publishing, FGDs and data work on new-user experience, a newbie AI-tips bot, anti-cheat monitoring for the Indonesian community.
March 2026: Apple Developer Academy Bali. Still thinks in PRDs and acceptance criteria; default stack Swift/SwiftUI/SwiftData, plus React and Godot.
Applying for fully-funded international master’s programs (IELTS 8.5). Freelance: web, iOS, voiceover, proposals — when the scope is clear.
How he works: concrete output over advice. Technical is fine. Direct, no padding. Push back if the idea is weak.

Also list education: ITS Surabaya, BSc Information Systems, GPA 3.83 (2019–2024); Monash University Melbourne, IISMA exchange, GPA 3.50 High Distinction (Jul–Nov 2022). Leadership one-liners: IISMA Alumni Club Community Engagement Director; Yada Youth Indonesia Vice Director; ITS MUN Club President. Certifications: IELTS 8.5, Duolingo 145/160, AWS Cloud Computing Graduate, SAP S/4HANA intro.

### Case studies — required structure
Eyebrow, title, pitch, role/team/stack, problem, user, what shipped, one PM+code decision, honest status (NO invented metrics).

CARA: Caregiver is the user, not the patient. Daily routines, checklist, Learn library (7 clinical categories), vitals, notes, seeded content. SwiftUI + SwiftData MVVM, iOS 26+, Liquid Glass, CI. Decision: safety rules live in the step (“if systolic BP < 100, hold the med and call the nurse”). Status: academy project, local-only, no App Store numbers.

ROBBIN: Team aileen, brent, lilo, gusti, kean. ARKit aim + Vision draw gesture Idle→Draw→Release. Endless survival. Crow vs Falcon. Combo scoring up to ×5. Game Center, Wanted Poster, TelemetryDeck. Decision: draw distance/speed = power. Status: open TODOs — reference art, second arrow type.

POVVY: Tagline “Memories, kept warm.” QR guest video messages → family keepsake. One event app, config not forks (content + theme + VITE_EVENT_ID). Cloudflare: Next landing povvy.id, Vite event app, Worker + R2 + Turnstile. Brand stationery paper #F8F3E9 / ink #2B2823 / wax #C2352B — that palette is Povvy’s product, NOT this portfolio’s UI. Decision: new event ≠ new codebase. Status: open — hero doodles, Povvy Hand glyphs, email capture → Pages Function + D1.

## Implementation notes
- Work rows: grouped list with chevron, not a Bento/Dribbble card grid of equal squares.
- Missing screenshots: labeled rectangles in --grouped, not Unsplash, not generated people.
- Favicon: “K”
- Footer inside window: © Kean · Bali · 2026
- Do not invent clients, download counts, or quotes.

Build the full multi-page site with real layout and these tokens applied everywhere, not a wireframe. Start with the window shell and home, then about and the three case studies.
```

---

## Open assets (flagged — do not silently fake)

- Headshot: none in this workspace. Skip, or use a typographic mark “K” until Kean adds one.
- CV PDF: `about/cv/CV Apr 2026 -Kennard-2.pdf` in this assistant folder — copy/export to the site as `/kennard-mahib-cv.pdf` when building.
- Product screenshots for Cara / Robbin / Povvy: not in this folder. Use labeled placeholders until dropped in.
- Domain: not specified. Build relative; deploy on Vercel.

## Changelog

- 2026-09-05 — First full brief + prompt. Direction: HIG dark website + macOS window chrome (desktop). Audience: personal brand, one thesis.
- 2026-09-05 — Site built at `portfolio-site/` (Next.js 16). `npm run dev` → http://localhost:3000. CV copied to `public/kennard-mahib-cv.pdf`. Screenshots still placeholders.
- 2026-09-15 — Site moved to `/Users/kean/Desktop/Personal Projects/2026-09-06 Portofolio`. Mockups in that folder were kept. `portfolio-site/` in this workspace is gone.
