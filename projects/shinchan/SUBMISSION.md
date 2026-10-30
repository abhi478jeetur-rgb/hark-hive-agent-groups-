# GapLens — Submission kit (Unstop → Rounds → Submit project)

## Fields
- Project name: GapLens — Light up the dark spots in your research
- GitHub: https://github.com/abhi478jeetur-rgb/gaplens (created Sat 10:00)
- Live demo: Vercel URL (Sat)
- Video: unlisted YouTube/Drive (Sun)
- PPT: GapLens.pdf (Sun)

## Description draft (finalise Sun with real numbers)
GapLens is an AI-assisted information gap detector. You ask a research question and add a few sources (links or pasted text). GapLens reads each source on the server, works out what a complete answer would need (eligibility, deadlines, documents, renewal rules…), and maps every source against that checklist.
The result is not a summary. It is a coverage map that shows:
• Confirmed facts, each with its exact quote and source link (quotes are checked against the source text in code)
• Dark spots: important questions none of the sources answer
• Conflicts: where sources disagree, shown side by side
• Possibly outdated or undated information
• A prioritised "Verify next" checklist with where to check
Every finding carries a label (Confirmed / Potential gap / Conflict / Possibly outdated) so users know what is evidence and what is an AI suggestion. It works in English and Hindi and exports a report.
Demo case: a student checking NSP post-matric scholarship rules across 5 web pages finds missing renewal conditions, a conflicting income limit and a 2024 article still ranking for 2026-27.
Tech: Next.js, TypeScript, Tailwind, Framer Motion/GSAP, Mozilla Readability, Groq (gpt-oss-120b, structured JSON), zod validation, deterministic scoring, Vercel. No login, no data stored.
Limitations: AI can miss or misjudge items; GapLens points to what to check and always asks users to confirm with the official source.

## README outline
Title + one-liner + live link + GIF · Problem · What it does (5 bullets) · How it works (pipeline diagram) · Evidence & transparency rules · Screenshots · Run locally (env GROQ_API_KEY) · Tech stack · Limitations & ethics · Built during Shinchan Online Hackathon 2026 (31 Oct–1 Nov).

## PPT (6 slides)
1. GapLens — title, tagline, Roshni
2. Problem — 5 tabs, 5 answers, missing pieces (scholarship example)
3. Solution — flow: Ask → Sources → Coverage map → Verify next
4. Demo screenshots — map, conflict, evidence drawer
5. How it works — pipeline + transparency safeguards (quote check, labels, scoring)
6. Impact & next — students first; roadmap: PDF/doc upload, browser extension, more languages
