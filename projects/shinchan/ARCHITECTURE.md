# GapLens — Architecture (frontend + backend), no code yet

## Stack
Next.js 15 App Router + TypeScript · Tailwind v4 + shadcn/ui · Framer Motion · GSAP · Lucide · @mozilla/readability + jsdom · zod (schema validation) · Groq (OpenAI-compatible, `https://api.groq.com/openai/v1/chat/completions`) · Vercel (Node runtime, maxDuration 60 s).

## Folder plan
```
app/
  page.tsx               landing
  analyze/page.tsx       workspace + results (client state machine)
  api/extract/route.ts   POST {url} -> {title, site, date, text, words}
  api/analyze/route.ts   POST {question, sources[], lang} -> Report (streams stage events)
components/              (see UIUX.md list)
lib/
  extract.ts             fetch + Readability + date detection
  chunk.ts               split text ~2.5K tokens, strip boilerplate
  llm.ts                 Groq client, JSON mode, retry/backoff, model fallback
  prompts.ts             aspect / evidence / synthesis prompts
  schema.ts              zod schemas for Aspect, Claim, Report
  verify.ts              quote substring/fuzzy check
  score.ts               deterministic coverage + priority
  i18n.ts                EN/HI strings
  report-md.ts           Markdown export
public/demo/scholarship.json   cached demo report
```

## Pipeline (api/analyze)
1. **Aspects** (1 LLM call): question → 6–10 aspects {id, label, why_it_matters, importance}.
2. **Evidence** (1 call per chunk, ≤ 8): chunk + aspects → claims [{aspect_id, statement, quote, value, date_mentioned, source_id}]. Prompt rule: quote must be copied exactly; if none, return nothing.
3. **Verify** (code): keep claim if quote ∈ source text (normalised whitespace; else fuzzy ≥ 0.9 → "unverified" label).
4. **Synthesis** (1 call): aspects + verified claims (compact) → per-aspect status, conflicts [{aspect_id, claim_a, claim_b, explanation}], outdated [{source_id, reason}], gaps [{aspect_id, why_missing_matters}], verify_next [{action, why, where, aspect_id}], summary sentence. Output language = lang.
5. **Score** (code): coverage %, priorities, heatmap matrix aspects × sources.
6. Stream stage events to client (ReadableStream, newline-delimited JSON: {stage, detail}) then final Report.

Rate-limit strategy: sequential calls, 2.5K-token chunks, 400 ms gap, on 429 read retry-after → wait → retry ×2 → fallback to openai/gpt-oss-20b. Total ≈ 10 calls per analysis → ~100 demo runs/day within 1,000 RPD.

## Report shape (contract between back and front)
Report { question, lang, createdAt, sources[{id,title,site,url,date,dateStatus:'dated'|'undated'|'old',words}], aspects[{id,label,importance,status:'covered'|'partial'|'missing'|'conflict',sourceIds[]}], facts[{id,aspectId,statement,quote,sourceId,verified}], gaps[...], conflicts[...], outdated[...], verifyNext[{id,priority:'high'|'med'|'low',action,why,where,aspectId}], coverage:number, summary }

## Date detection (extract.ts)
meta article:published_time / article:modified_time / og:updated_time → JSON-LD datePublished/dateModified → <time datetime> → regex on visible text ("Updated on 12 Sep 2026", "Last date: 31-10-2026", "2026-27"). Outdated rule: newest date > 12 months old, or academic year in text ≠ current, or no date → undated.

## Frontend state machine (analyze page)
idle → editing → extracting (per source) → ready → analysing (stages) → results | error. Report saved to localStorage; Export reads it. Lang toggle re-calls synthesis only (cached aspects/claims).

## Security / ops
GROQ_API_KEY in Vercel env only. Server fetch blocks private IPs, 10 s timeout, 2 MB cap. No user data stored. Vercel deploy via CLI token (Hark) from GitHub repo abhi478jeetur-rgb/gaplens (public, real commit times starting 31 Oct 10:00 IST).
