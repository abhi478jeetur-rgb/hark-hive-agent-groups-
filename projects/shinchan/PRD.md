# GapLens — Product Requirements Document
Shinchan Online Hackathon 2026 · Problem: "Digital Dark Spot — AI-Assisted Information Gap Detection Platform"
Status: planning (written 30 Oct 2026, before build window). No code exists yet. Build: 31 Oct 10:00 IST → submit by 1 Nov 17:00 IST (target 15:00).

## 1. One-liner
GapLens shines a light on what your sources *don't* tell you. Ask a question, add sources, and it shows what is confirmed (with quotes), what is missing, what conflicts, what is outdated — and exactly what to verify next.

## 2. Problem
People making real decisions (students applying for scholarships, first-time job seekers, families checking a government scheme) read 4–6 web pages that each cover part of the picture. They cannot easily see:
- which essential questions **no** source answers (dark spots),
- where two sources **disagree** (income limit, last date, documents),
- which information is **old or undated**,
- what to check next and where.
Chatbots and summaries make this worse: they blend everything into one confident answer and hide the gaps.

## 3. Target users
- Primary: Indian students (16–25) researching scholarships / admissions / exams. Hindi + English.
- Secondary: anyone doing quick decision research (journalists, researchers, parents).

## 4. Goals (mapped to judging)
| Judging criterion | Weight | How GapLens wins it |
|---|---|---|
| Working prototype | 25% | Live Vercel link; demo works end-to-end in < 30 s; preloaded demo + bring-your-own sources |
| Innovation | 20% | "Expected aspects" checklist per question → coverage heatmap → dark spots; flashlight reveal UX |
| Problem relevance | 15% | Scholarship case with real conflicting Indian sources |
| Technical implementation | 15% | Server extraction (Readability), chunked structured LLM pipeline, schema validation, deterministic scoring |
| Evidence / transparency | 15% | Every claim = quote + source + link; labels: Confirmed / Potential gap / Conflict / Outdated; confidence + "why flagged" |
| Presentation / demo | 10% | Polished dark UI, mascot Roshni, 2-min video, 6-slide PPT |

Non-goals: accounts/login, database, crawling the whole web, giving final legal/financial advice.

## 5. Core user flow
1. Landing → "Try the scholarship demo" or "Start your own".
2. **Ask**: type research question (e.g. "NSP post-matric scholarship 2026-27: am I eligible and what do I need to renew?").
3. **Sources**: paste 2–6 URLs and/or paste text. Each shows extraction status (title, site, date found / undated, word count).
4. **Analyse** (button "Find the dark spots"): progress in 4 visible stages — Reading sources → Mapping what a complete answer needs → Matching evidence → Finding gaps & conflicts.
5. **Results dashboard**:
   - Coverage score (e.g. 58% "partly lit") + one-line verdict.
   - Coverage heatmap: rows = expected aspects (eligibility, income limit, documents, deadline, renewal rules, amount, how to apply, official contact), columns = sources; cell = covered / partial / missing / conflicting.
   - Tabs: **Confirmed facts** (quote + source chip) · **Dark spots** (missing) · **Conflicts** (side-by-side quotes) · **Outdated / undated**.
   - **Verify next** checklist: prioritised (High/Med/Low), each with why, where to check (official link if known), and a checkbox.
6. Click any finding → **Evidence drawer** opens with the source text, quote highlighted.
7. Toggle **English / हिंदी**. Export **Markdown report** (and Print-to-PDF).

## 6. Functional requirements
F1 Question input (10–300 chars), with 3 example chips.
F2 Source input: up to 6 URLs + pasted text blocks; dedupe; remove.
F3 Server-side extraction: fetch URL (timeout 10 s, 2 MB cap), Readability → clean text, title, site name, published/modified date (meta tags, JSON-LD, visible "updated on" regex). PDFs: text extraction if time allows, else ask user to paste text.
F4 Aspect generation: LLM produces 6–10 "expected aspects" a complete answer needs, each with importance (critical/important/nice).
F5 Evidence extraction per source (chunked): claims with exact quote (must be substring of source text), aspect id, value, date mentioned.
F6 Quote verification (deterministic): drop/flag any quote not found in source text (fuzzy match ≥ 0.9) → label "unverified".
F7 Synthesis: per aspect → status covered / partial / missing / conflicting; conflicts list with both quotes; outdated flags (date older than 12 months or academic year mismatch, or undated).
F8 Scoring (deterministic, in code, not LLM): coverage = Σ(weight × status score) / Σ weight; critical=3, important=2, nice=1; covered 1, partial 0.5, conflict 0.25, missing 0.
F9 Verify-next checklist: generated from missing/conflict/outdated items, priority = importance × severity; each item: action, why, suggested place to verify (prefer official domain found among sources).
F10 Labels everywhere: "Confirmed in N sources", "Potential gap", "Conflict", "Possibly outdated", "Unverified quote", plus AI-suggestion marking (purple) vs source fact (green).
F11 Language toggle: UI strings + LLM output language (re-run synthesis in Hindi, quotes stay original).
F12 Export: Markdown download; print stylesheet for PDF.
F13 Demo mode: preloaded scholarship question + sources + cached result JSON (works even if API is rate-limited).
F14 Error states: URL blocked/failed → "Couldn't read this page. Paste its text instead." Rate limit → retry with backoff, then cached demo note.

## 7. Non-functional
- First result < 30 s for 4 sources; Groq free plan: 30 RPM, 8K tokens/min, 1,000 req/day on openai/gpt-oss-120b → cap each chunk ~2.5K tokens, ≤ 4 sources × 2 chunks, sequential with small delay; fallback model openai/gpt-oss-20b.
- No data stored server-side; state in browser (localStorage for last report).
- Accessibility: keyboard nav, focus rings, contrast AA, prefers-reduced-motion.
- Mobile responsive (judges may open on phone).
- Keys only in Vercel env (GROQ_API_KEY); never in repo.

## 8. Success metrics for demo
- Demo finds ≥ 2 real gaps, ≥ 1 conflict, ≥ 1 outdated/undated source on the scholarship case.
- 100% of displayed quotes verifiable in the source text.
- Zero crashes on 5 test cases (see DEMO.md).

## 9. Risks & mitigations
| Risk | Mitigation |
|---|---|
| Groq rate limit / token cap | Chunking, trimming boilerplate, cached demo result, 20b fallback |
| Sites block fetch (gov sites, Cloudflare) | Paste-text fallback; demo sources pre-tested Saturday 10:15 |
| LLM invents quotes | Deterministic quote check (F6) |
| Time overrun | Strict P0/P1/P2 cut list (TOMORROW.md) |
| Fake-looking "AI summary" | Gaps-first UI; heatmap and verify-next are the hero, not prose |

## 10. Priorities
- P0 (must, by 16:00 Sat): question + sources → extraction → aspects → evidence → gaps/conflicts/outdated → checklist → results UI with evidence drawer; deployed.
- P1 (by 22:00 Sat): heatmap, coverage score, demo mode, Markdown export, Roshni animation, Hindi toggle.
- P2 (if time): PDF upload, print PDF, share link (base64 state in URL), dark/light, source credibility hint (gov/edu domain badge).
