# GapLens theme: Torchlight Archive (final, 30 Oct 2026)
Chosen with skills: theme-factory (10 presets + custom method), frontend-design (anti-generic review), web-artifacts-builder style rule (no purple gradients / Inter / uniform radius).

## Why this theme
Scored the 10 theme-factory presets against the brief (evidence & trust 15%, presentation 10%, flashlight "dark spot" metaphor, Hindi readability, long reading sessions):
- Ocean Depths (navy + teal, "trust-building") fit best on trust and readability but has no light/dark-spot story.
- Tech Innovation / Midnight Galaxy read as generic AI (neon blue, purple) — rejected.
- Golden Hour has the torch amber but a light beige base hides the "dark spot" idea.
Result: a custom theme = Ocean Depths' navy + seafoam (trust) + Golden Hour's torch amber (dark spots / light) + coral for conflicts.

## Tokens
| Name | Hex | Role |
|---|---|---|
| night | #0E1524 | page background |
| dusk | #1A2332 | panels, drawer (Ocean Depths navy) |
| line | #2C384E | borders, empty cells |
| torch | #FBBF24 | dark spots, primary CTA, beam, score |
| seafoam | #5EC4B6 | confirmed source facts (partial: #346260) |
| coral | #F27F6B | conflicts |
| lavender | #A78BFA | AI-suggested / inferred tag only (small, never gradients) |
| cream | #F1FAEE | main text |
| fog | #94A3B8 | secondary text |
Contrast: cream on night 16:1, fog on dusk 6:1, night text on torch 11:1. Seafoam vs coral also distinguishable for red-green colour blindness (luminance differs) and every status also has an icon/label.

## Type
- Display: Bricolage Grotesque (700, tight tracking -1%)
- UI/body: Instrument Sans (400/600), 16/1.55
- Hindi: Mukta (400/600)
All OFL, Google Fonts via next/font.

## Shape & motion
Radii: 14 panels, 8 cells/chips, 12 buttons. No drop shadows; depth from torch glow only. One hero motion: beam reveal on the coverage map.

Preview: theme-torchlight-archive.png

## Anti-slop audit (avoid-ai-design skill, 30 Oct 2026)
Plan reviewed against SD1–SD8 + C7:
- Dark ground is earned (C7 ok): the product's idea is torchlight finding dark spots; palette is navy + 4 job-bound colours, not one neon on black (not SD2).
- Seafoam has a job (= confirmed status), never decorative (SD8 ok). Amber = dark spots/primary action only.
- Fonts not Inter/Geist/Roboto. No serif-italic garnish.
- Headline carries no single accented word (SD5).
Build bans: no ALL-CAPS eyebrows or mono labels (mono only for quotes' source URLs if needed), no `·` metadata strings, no → glued on CTAs, no 01/02/03 except the genuinely ranked Verify-next list, no three-icon-card feature row, no fake macOS window, no rounded-2xl+shadow on everything, no fade-up on every section (one signature motion: beam reveal), shadcn only if re-themed to these tokens. Every interactive element has hover + :focus-visible; reduced-motion respected.
Gate before every deploy: `node /workspace/work/skills/avoid-ai-design/scripts/detect.mjs src` → no P0/P1 unless marked `avoid-ai-design-ignore`, plus desktop/mobile screenshot silhouette test.
