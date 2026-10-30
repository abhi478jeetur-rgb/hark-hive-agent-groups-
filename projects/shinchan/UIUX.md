# GapLens — UI/UX & Motion Spec
Design guidance source: frontend-design skill (installed 30 Oct). Moodboard: inspiration/ (16 refs) + moodboard.jpg.

## 1. Design plan (pass 1 → reviewed → revised)
Subject: a torch in a dark archive. Audience: students and researchers. Primary job: make missing information visible.

Colour (revised): not pure near-black + one neon (generic tell #2) — a deep **ink-navy night** with warm torchlight.
| Token | Hex | Use |
|---|---|---|
| night | #0B1020 | page background |
| dusk | #141B2E | panels, drawer |
| torch | #FBBF24 | light beam, dark-spot highlights, primary CTA |
| leaf | #22C55E | confirmed source facts |
| ember | #F87171 | conflicts |
| dream | #A78BFA | AI suggestions / inferred items |
| paper | #E5E7EB | text |
| fog | #94A3B8 | secondary text |

Type (revised from Space Grotesk + Inter, which is the default pairing): **Bricolage Grotesque** (display, variable width — headline widths can "stretch" as the beam passes) + **IBM Plex Sans** (body/UI) + **Mukta** (Devanagari, matches Plex x-height). Scale 1.25: 13 / 16 / 20 / 25 / 31 / 39 / 61. Body 16/1.55, max 72ch. Sentence case everywhere; no all-caps labels, no mono labels, no "→" on buttons.

Layout: left-aligned, asymmetric. Not a grid of identical cards — results use one big **map** (heatmap) + a **reading column**, with hierarchy shown by size, not boxes. Radii by role: 14px panels, 8px chips, 999px status pills.

Principles:
1. Darkness is the default; light is earned by evidence. Covered things glow, missing things stay dark with an amber outline.
2. Spend boldness in one place: the beam reveal on the heatmap. Everything else calm.
3. Every glowing thing is clickable to its quote.
4. Copy says what the user does: "Find the dark spots", "Add a source", "Open quote", "Mark as checked".

## 2. Screens (ASCII wireframes)

### Landing (/)
```
 GapLens                                             [English | हिंदी]
 ──────────────────────────────────────────────────────────────────────
  (dark page; a soft torch cone follows the cursor, revealing faint text
   fragments behind: "last date?", "income limit?", "renewal?")

  See what your sources                     [ Roshni mascot, torch on ]
  don't tell you.
  Add a few links. GapLens shows what's confirmed, what's
  missing, what disagrees, and what to check next.

  [ Try the scholarship demo ]   Start your own

  ── three plain lines, no cards ──
  ● Confirmed  every fact keeps its quote and link
  ● Dark spots  questions none of your sources answer
  ● Verify next  a checklist ranked by what matters most
```

### Workspace (/analyze) — step 1 & 2 on one page
```
 Your question
 [ NSP post-matric scholarship 2026-27: eligibility and renewal?   ]
   examples: (Scholarship renewal) (College admission) (Exam rules)

 Sources  (2–6)                                         [ + Add a source ]
 ┌ scholarships.gov.in   "NSP Students"   updated 2026  ✓ 1,240 words  ✕
 ├ righttoinformation.wiki  "Renew your NSP…"  2026      ✓ 2,100 words  ✕
 ├ sarkariworld.com  "NSP last date…"  19 Sep 2026       ✓ 1,800 words  ✕
 └ careers360.com  "Post matric…"  undated ⚠            ✓ 3,000 words  ✕
   or paste text ▸

                                     [ Find the dark spots ]
```

### Analysing (overlay on workspace, ~10–25 s)
```
   Roshni sweeps her torch left→right across 4 source "pages"
   1 Reading sources            ✓
   2 Mapping a complete answer  ✓  8 things a full answer needs
   3 Matching evidence          …  23 quotes found
   4 Finding gaps & conflicts
```

### Results (/analyze#report)
```
 NSP post-matric scholarship 2026-27…            [Export] [हिंदी] [New]
 ──────────────────────────────────────────────────────────────────────
  58%  partly lit                     3 dark spots · 2 conflicts · 1 old
  "Your sources agree on how to apply but say little about renewal
   marks and disagree on the income limit."
 ──────────────────────────────────────────────────────────────────────
  COVERAGE MAP                        │  VERIFY NEXT
            NSP  RTI  Sarkari  C360   │  ☐ High  Confirm income limit for
  Eligibility ██   ██   ░░      ██    │         your exact scheme
  Income lim. ██   ··   ▓▓!     ▓▓!   │         why: 2 sources disagree
  Documents   ░░   ██   ··      ██    │         where: scheme guidelines PDF
  Last date   ██   ··   ██      ··    │  ☐ High  Find renewal marks rule
  Renewal     ··   ██   ··      ··    │  ☐ Med   Check if C360 page is
  Amount      ··   ··   ··      ··  ◀ dark spot (amber outline)
  Contact     ··   ··   ··      ··    │
                                       │
  [Confirmed 9] [Dark spots 3] [Conflicts 2] [Outdated 1]
  ─ Conflict: income limit ─────────────────────────────
   Sarkari: "…₹2.5 lakh…"        vs   NSP guideline: "…₹8 lakh…"
   [Open quote] [Open quote]     Label: Conflict · confidence medium
```
██ covered (glow green) · ▓▓! conflict (ember) · ░░ partial · ·· missing (dark, amber outline when the whole row is dark = dark spot)

### Evidence drawer (right side, 420px; bottom sheet on mobile)
Source title + domain + date badge → scrollable clean text, matched quote highlighted with torch-yellow underline, auto-scrolled into view; "Open original page" link; "Quote verified ✓ / Unverified ⚠".

### Mobile
Single column: score → verify next → tabs → heatmap becomes horizontally scrollable with sticky aspect column.

## 3. Components (shadcn/ui base, restyled)
QuestionInput, ExampleChips, SourceList/SourceRow (status: reading, read, failed, undated), PasteTextDialog, AnalyzeButton, StageProgress, Roshni (SVG), CoverageScore (animated number + ring), CoverageMap (CSS grid, not a chart lib), FindingTabs, FactItem, GapItem, ConflictPair, OutdatedItem, VerifyChecklist, EvidenceDrawer, LangToggle, ExportMenu, EmptyState, ErrorBanner, Toast.

## 4. Motion spec
Rule: one orchestrated moment + motion that answers actions. Respect prefers-reduced-motion (all become instant fades).
| Moment | Trigger | Animation | Tool | Duration |
|---|---|---|---|---|
| Cursor torch (landing only) | mouse move | radial-gradient mask follows cursor (CSS vars updated via rAF) | vanilla + CSS | — |
| Roshni idle | page load | gentle bob 4px, blink every 4–6 s | Framer Motion | loop |
| Source added | user adds URL | row slides in from 8px, status spinner → check | Framer | 200 ms |
| Analysing | click analyse | Roshni's beam sweeps across 4 page icons; stage list ticks | GSAP timeline | 1.2 s loop |
| **Beam reveal (hero moment)** | results arrive | dark heatmap; a cone of light sweeps rows top→bottom, cells light up green/ember as passed; missing rows stay dark and pulse amber once | GSAP timeline, stagger 40 ms | ~1.6 s once |
| Score count-up | after reveal | 0→58% number + ring stroke | Framer animate | 800 ms |
| Tab switch | click | underline slides (layoutId) | Framer | 180 ms |
| Open evidence | click finding | drawer slides from right, quote highlight sweeps left→right | Framer | 250 ms |
| Checklist tick | check item | strike-through draws, item dims | CSS | 200 ms |
No fade-up on every section; no hover lift on every card.

## 5. Roshni mascot
Original SVG: small pocket-torch body (rounded, amber #FBBF24 with dusk-navy band), two dot eyes + small smile on the lens ring, tiny arms. States: idle (soft glow), searching (beam sweeping), found (beam widens, eyes happy), worried (dim, for errors), sleeping (empty state). Built as inline SVG with named groups so Framer/GSAP animate beam opacity/rotation. Inspiration refs 13/14 only for proportion — design is our own.

## 6. Copy deck (EN / HI)
| Key | English | हिंदी |
|---|---|---|
| hero | See what your sources don't tell you. | जानिए आपके स्रोत क्या नहीं बता रहे। |
| sub | Add a few links. GapLens shows what's confirmed, what's missing, what disagrees, and what to check next. | कुछ लिंक जोड़िए। GapLens बताएगा क्या पक्का है, क्या गायब है, कहाँ बातें टकराती हैं, और आगे क्या जाँचना है। |
| demo | Try the scholarship demo | स्कॉलरशिप डेमो आज़माइए |
| analyse | Find the dark spots | अंधेरे कोने खोजिए |
| addSource | Add a source | स्रोत जोड़िए |
| confirmed | Confirmed | पक्की जानकारी |
| gap | Potential gap | संभावित कमी |
| conflict | Conflict | टकराव |
| outdated | Possibly outdated | शायद पुरानी |
| verify | Verify next | आगे यह जाँचें |
| openQuote | Open quote | उद्धरण देखें |
| failRead | Couldn't read this page. Paste its text instead. | यह पेज नहीं पढ़ पाए। उसका टेक्स्ट पेस्ट करें। |
| rate | Too many requests right now. Retrying in a few seconds. | अभी बहुत अनुरोध हैं। कुछ सेकंड में फिर कोशिश हो रही है। |
| empty | Add a question and two sources to start. | शुरू करने के लिए एक सवाल और दो स्रोत जोड़िए। |
| disclaimer | GapLens points to what to check. Always confirm on the official source. | GapLens बताता है क्या जाँचना है। अंतिम पुष्टि हमेशा आधिकारिक स्रोत से करें। |
