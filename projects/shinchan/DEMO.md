# GapLens — Demo data, test cases, video script

## Demo question
"NSP post-matric scholarship 2026-27: who is eligible, what documents are needed, and how do I renew?"

## Demo sources (picked to contain real gaps/conflicts; re-test Sat 10:15)
1. https://scholarships.gov.in/ — official; renewal dates (31-10-2026, institute 15-11-2026), OTR mandatory, AY 2026-27 opened 1 Jun 2026. Little on income limits/documents → gaps.
2. https://righttoinformation.wiki/education/nsp-scholarship-renewal — renewal guide; says each scheme sets its own date; OTR once per career.
3. https://www.sarkariworld.com/nsp-scholarship-last-date-2026-27 — third-party dates (pre-matric 30 Sep, post-matric 31 Oct; UP renewal 15 Oct) → possible conflicts with scheme-wise dates.
4. https://school.careers360.com/articles/post-matric-scholarship — published 2024, updated text; income limit ₹2.5 lakh for minorities → date/outdated + income-limit conflict.
5. https://www.shiksha.com/boards/articles/post-matric-scholarship-2026-27-list-of-scholarships-eligibility-amount-last-date-and-apply-online-blogId-240745 — "Class 11–12", ₹2.5 lakh limit → scope conflict (post-matric also covers UG/PG).
Backup official PDF (paste text if needed): https://scholarships.gov.in/public/schemeGuidelines/POST_MATRIC_OBC_GUIDELINES.pdf
Expected findings: dark spots = renewal marks/attendance rule, scholarship amount, helpline/contact; conflicts = income limit (2.5 L vs scheme-specific), eligible classes; outdated = 2024-published article.

## Test cases
| # | Input | Expect |
|---|---|---|
| T1 | Demo above (5 URLs) | ≥2 gaps, ≥1 conflict, ≥1 outdated, all quotes verified |
| T2 | 2 sources only, pasted text | works, lower coverage |
| T3 | One URL that blocks fetch | row shows "Couldn't read…", analysis continues with others |
| T4 | Hindi question "झारखंड ई-कल्याण छात्रवृत्ति की अंतिम तिथि?" + ekalyan.cgg.gov.in + careers360 Jharkhand page | Hindi output, undated flag |
| T5 | Non-scholarship: "Is the new iPhone waterproof rating IP68 true?" + 2 articles | generic aspects still sensible |
| T6 | Groq 429 simulated | retry message, then success or cached demo note |

## 2-minute video script
0:00 Hook (landing, cursor torch): "Every source tells you part of the story. GapLens shows the parts nobody told you."
0:12 Problem: 5 scholarship pages, different dates and limits.
0:25 Demo: type question, click "Try the scholarship demo", sources load with dates (one undated ⚠).
0:40 "Find the dark spots" → Roshni searching → beam reveal on coverage map.
1:00 Score 58%, open a dark spot (renewal rule), open a conflict (income limit) → evidence drawer with highlighted quotes.
1:25 Verify next checklist, tick one; switch to हिंदी.
1:40 Export report. Tech: Readability extraction, Groq structured output, quote verification, deterministic scoring.
1:55 Close: "GapLens: light up what's missing before you decide."
