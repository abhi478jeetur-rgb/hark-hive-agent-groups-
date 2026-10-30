# GapLens — Build Day Runbook (Sat 31 Oct → Sun 1 Nov 2026, IST)
Hark-One builds; Abhijeet reviews and submits. Hark starts automatically at 10:00 IST (scheduled).

| Time (IST) | Who | Task | Done when |
|---|---|---|---|
| Sat 10:00 | Hark | Create public repo `gaplens`, Next.js + Tailwind + shadcn scaffold, first commit, Vercel project + GROQ_API_KEY env, first deploy | Live URL shows landing stub |
| 10:15 | Hark | Test-fetch the 5 demo sources via /api/extract | All readable or paste-text saved |
| 10:30–12:30 | Hark | P0 backend: extract, chunk, Groq client, aspects + evidence + verify + synthesis + score | /api/analyze returns valid Report for demo |
| 12:30 | Hark → you | Update: repo + live link | You open it |
| 12:30–15:30 | Hark | P0 frontend: question, sources, analyse stages, results tabs, verify checklist, evidence drawer | Full flow works on live URL |
| 15:30–16:00 | Hark | P0 checkpoint: run 5 test cases, fix crashes, deploy | P0 complete |
| 16:00–19:00 | Hark | P1: coverage map + beam reveal, score, demo mode cache, Roshni SVG + states | Demo looks finished |
| 19:00–21:00 | Hark | P1: Hindi toggle, Markdown export, mobile pass, a11y, reduced-motion | |
| 21:00–22:00 | Hark | README with screenshots, architecture diagram, limitations | |
| 22:00 | you | 10-min review on phone + laptop; tell Hark anything you dislike | |
| Sun 08:00–11:00 | Hark | Fixes from review, P2 if time, final deploy, freeze code | Code freeze 11:00 |
| 11:00–12:30 | Hark | PPT (6 slides) + Unstop description draft + demo video script | Files ready |
| 12:30–14:00 | you | Record 2-min screen video (script in DEMO.md), upload unlisted YouTube/Drive | Link works in incognito |
| 14:00–15:00 | you | Unstop → Rounds → submit: name, description, GitHub, live link, video, PPT | Submission confirmation screenshot |
| 15:00–17:00 | buffer | | Deadline 17:00 |

Cut list if behind at 16:00: drop Hindi re-run (keep UI strings only) → drop export → drop beam GSAP (CSS stagger instead). Never cut: quotes + verify-next + live link.
