# Shinchan Online Hackathon 2026 (Devengers, Unstop) — "GapLens"

- Solo entry: Abhijeet (registered + fee paid on Unstop, 30 Oct 2026). Builder: Hark-One.
- Official problem statement (problem-statement.pdf, from the WhatsApp channel): "DIGITAL DARK SPOT — AI-Assisted Information Gap Detection Platform". Fixed problem, NOT open innovation.
- Build: 31 Oct 2026 10:00 AM IST -> submission deadline 1 Nov 2026 5:00 PM IST.
- Submit on Unstop with the same account: Rounds section -> project submission button (opens 31 Oct 10:00 AM).
  - Mandatory: project name, detailed project description (problem, solution, how it works, features, innovation, stack, future scope), GitHub repo link (public, README).
  - Optional (we do all): live demo link, demo video, PPT.
- Rule we follow: no code/repo before 10:00 AM 31 Oct. Tonight = plan, design, accounts, keys only.

## Judging (10 marks)
Problem understanding 15% | Innovation 20% | Working prototype 25% | Technical 15% | Evidence/accuracy/transparency 15% | Presentation 10%.
Guidance: polished core > many half features; real or clearly labelled sample sources; AI findings labelled as "potential" signals; every finding clickable to its source; a generic chatbot/summary fails.

## Must-have workflow (= suggested demo flow)
1. User enters a research question/topic (e.g. "What should I verify before applying for NSP Post-Matric scholarship?").
2. Add sources: paste URLs (server fetches + extracts text and page date), paste text, and optional "Find sources" (Gemini with Google Search grounding, clearly marked).
3. Extraction: key facts per source, each fact = claim + source + exact quote snippet + date.
4. Analysis cards:
   - Sourced summary (only facts with citations).
   - Gaps: expected aspects for this kind of decision (AI builds an "expected checklist", e.g. eligibility, deadline, documents, renewal, fees, official link) vs what sources actually cover -> "Not found in sources reviewed".
   - Conflicts: same aspect, different values across sources, both quotes side by side.
   - Outdated: page date / cycle year older than current, or undated.
5. Prioritised "Verify next" checklist (High/Med/Low), each item says where to verify (official source).
6. Dashboard visually separates: Sourced fact (green, cited) | AI suggestion (purple, labelled) | Uncertain (amber).
7. Click any finding -> source panel with highlighted quote + link.
8. Coverage score ("Information completeness 62%") + export report (PDF/Markdown).
Innovation hooks: "expected-aspect map" per decision type, coverage heatmap (aspects x sources grid showing which source covers what — the "dark spots"), Hindi/English toggle for output.

## Stack (free)
- Next.js (App Router, TypeScript) + Tailwind + shadcn/ui; Motion (Framer Motion) + GSAP for animation; Lucide icons.
- Fetching: server route fetch + @mozilla/readability + jsdom; date from meta tags/JSON-LD/visible text.
- AI: Groq API (free, openai/gpt-oss-120b, JSON output; 30 RPM, 1,000 RPD, 8K TPM -> chunk sources). Gemini free quota was used up; Gemini only as backup. Source discovery: user URLs + optional search.
- No database: state in browser; sample demo sessions as JSON (clearly labelled real sources).
- Deploy: Vercel. Repo public on abhi478jeetur-rgb, MIT.

## Design (confirm with Abhijeet)
- Theme: "spotlight in the dark" — dark navy canvas, dark spots glow when found.
- Palette: night #0B1020, panel #141B2E, spotlight amber #FBBF24 (gaps), sourced green #22C55E, AI purple #A78BFA, conflict red #F87171, text #E5E7EB.
- Fonts: Space Grotesk (headings), Inter (body), Noto Sans Devanagari for Hindi.
- Mascot: small torch/flashlight character "Roshni" that sweeps light over the dashboard while analysing.

## Timeline (IST)
- 31 Oct 10:00 repo + skeleton + Vercel deploy
- 10:30-14:00 source input + fetch/extract + fact extraction with citations
- 14:00-18:00 gaps, conflicts, outdated detection + checklist + source panel
- 18:00-22:00 dashboard UI, heatmap, animations, Hindi toggle, export
- 22:00-24:00 demo sessions (scholarship case with real sources), README
- 1 Nov 08:00-12:00 polish, PPT, demo video (2-3 min), project description
- 1 Nov by 15:00 Abhijeet submits on Unstop (2h buffer)

## Abhijeet's to-dos tonight
- Free Groq API key (console.groq.com/keys) saved in Hark form; Vercel classic token (vercel.com/account/tokens) so Hark-One deploys via CLI.
- Vercel account (sign in with GitHub) ready.
