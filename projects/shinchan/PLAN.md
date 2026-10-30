# Shinchan Online Hackathon (Devengers, Unstop) — "Kavach"

- Solo entry: Abhijeet (registered + fee paid on Unstop, 30 Oct 2026).
- Build window: 31 Oct 2026 10:00 AM IST -> 1 Nov 10:00 AM IST. Submit on Unstop (competition page, "Submission through Unstop only" round) by 1 Nov 5:00 PM IST. Updates on the mandatory WhatsApp channel.
- Rule we follow: NO code, repo or build before 10:00 AM 31 Oct. Tonight = idea, plan, design, accounts, keys only.
- Builder: Hark-One. Hark-Two not involved (solo event).

## Idea: Kavach — AI scam shield for Indian families
Problem: UPI/KYC/"digital arrest"/job/lottery scams on SMS & WhatsApp; parents and grandparents can't tell real from fake.
User pastes a message, a link, or uploads a screenshot. Kavach:
1. Gives a big verdict: Safe / Suspicious / Scam, with a confidence meter.
2. Explains red flags in simple Hindi, Hinglish or English (urgency, fake link, OTP ask, lookalike domain).
3. Tells exactly what to do now (don't share OTP, call 1930, report at cybercrime.gov.in, block number).
4. Reads the answer aloud in Hindi (browser speech, free) for elders.
5. "Practice mode": a mini quiz of real-looking fake messages to train family members (gamified, Shinchan-playful).
6. Avatar mascot "Kavach Dost" that reacts (happy on safe, alarmed on scam).

## Stack (free)
- Next.js (App Router) + Tailwind + shadcn/ui, Motion (Framer Motion) + GSAP for animation, Lottie mascot, canvas-confetti.
- Gemini API (free tier, vision + text) via a server route; key never in browser.
- Deploy: Vercel. Repo: public on abhi478jeetur-rgb, MIT.

## Design (to confirm with Abhijeet)
- Palette: deep indigo #1E1B4B (trust), shield teal #14B8A6 (safe), alert red #EF4444 (scam), amber #F59E0B (suspicious), soft cream #FFF8EE bg.
- Fonts: Bricolage Grotesque headings, Mukta body (Devanagari).
- UX: one giant input box + "Check karo" button; result card animates in; 3 taps max.

## Timeline 31 Oct (IST)
- 10:00 repo + skeleton + deploy hello
- 11:00-15:00 check flow (text, link, screenshot) + verdict card + Hindi explain
- 15:00-18:00 read-aloud, language switch, practice quiz, mascot
- 18:00-21:00 polish, animations, mobile, error states, 15-message test set accuracy
- 21:00-23:00 README (problem, demo GIF, features, architecture, setup)
- 1 Nov 07:00-10:00 demo video (2-3 min) + final deploy; stop coding at 10:00
- 1 Nov by 14:00 Abhijeet submits on Unstop (repo link, live link, video, description)

## Abhijeet's to-dos tonight
- Create a free Gemini API key at https://aistudio.google.com/apikey and save it in Hark's secure form.
- Have a Vercel account (sign in with GitHub) ready.
