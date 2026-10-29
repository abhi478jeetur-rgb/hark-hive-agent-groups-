# DSH Hacks V2: "Parchi" (AI x Healthcare)

- Owner: Hark-Two (builds). Hark-One reviews. Abhijeet approves public steps and submits.
- Hackathon: https://dsh-hacks-v2.devpost.com/ (rules: /rules, resources: /resources)
- Deadline: Nov 14, 2026 11:45 PM PST = **Nov 15, 2026 1:15 PM IST**. Internal target: submit by **Nov 13, 2026 9:00 PM IST**.
- Eligibility: ages 13+, students only, all countries. Solo OK. Abhijeet enters under his real name.
- Prizes: non-cash (1st: Momen $2,000 credits, Adaption Labs $1,000 credits, CodeCrafters VIP, etc.; up to 100 teams get Tin Computer $299 credits; YRI 50% research-fellowship scholarship for Best Research-Oriented Project). Value = credits + a strong portfolio/college-application project.
- Judging: Idea (problem fit, innovation, impact), Implementation (works, technically impressive), Design (UX, interface), Presentation (clearly defines and addresses the problem).

## Submission requirements (from the official page)
1. Project: website/app/prototype with real user interaction.
2. Demo video: purpose, features, how a user interacts.
3. One-page project description as a PDF.
4. GitHub repository (or code PDF).

## The idea: Parchi
Problem: in India, many patients (especially elderly and rural) can't read a doctor's handwritten prescription, don't know what each medicine is for, when to take it, or that a much cheaper generic (Jan Aushadhi) exists.
Solution: a mobile-first web app. User snaps a photo of a prescription or medicine strip, then Parchi:
- reads it with an AI vision model and lists each medicine (name, strength, dose, timing);
- explains each one in simple Hindi, Hinglish or English (what it's for, how to take it, common side effects, food/alcohol warnings);
- builds a daily dose schedule (morning/afternoon/night, before/after food) with browser reminders;
- shows the generic salt and, where available, a cheaper Jan Aushadhi equivalent with price comparison;
- flags low-confidence reads ("please confirm with your pharmacist") and always shows a "not medical advice" note;
- optional "read aloud" in Hindi for low-literacy users (browser speech synthesis, free).
Research angle (for the YRI prize): measure reading accuracy on a small test set (10 to 20 sample prescriptions, synthetic or with personal info removed) and report it in the PDF and README.

## Stack (all free)
- Frontend: React + Vite (or Next.js), Tailwind, mobile-first, PWA-installable. Clean, calm, warm design.
- AI: Google Gemini API free tier (vision + text) via a small serverless function so the key never reaches the browser. Key from https://aistudio.google.com (Abhijeet creates it and saves it in Hark-Two's secure vault, never in the repo).
- Data: Jan Aushadhi product list (public, from the PMBI / janaushadhi.gov.in site) converted to JSON for generic lookup.
- Hosting: Vercel or Appwrite Sites free tier.
- Storage: none server-side by default; schedule saved in localStorage (privacy-first, say so in the pitch).

## Build plan with dates (IST)
- Oct 30 to Nov 1: read rules/resources/FAQ, confirm a new project is fine; set up repo `parchi` on abhi478jeetur-rgb (public, MIT), skeleton app, Gemini function working on one image.
- Nov 2 to Nov 6: prescription reading + explanation + language switch + schedule + reminders; Jan Aushadhi lookup.
- Nov 7 to Nov 9: design polish, read-aloud, error/low-confidence states, test set + accuracy numbers.
- Nov 10 to Nov 11: README (top-quality: problem, demo GIF, features, architecture, accuracy, setup, disclaimer), one-page PDF, video script.
- Nov 12: demo video (2 to 3 min) recorded and edited; Devpost draft filled.
- Nov 13: Abhijeet reviews, Hark-Two fixes, Abhijeet submits by 9:00 PM IST.

## Demo video plan (2 to 3 min)
- 0:00 to 0:20 hook: a real-looking handwritten prescription, "Can you read this? Most patients can't."
- 0:20 to 0:40 problem with 1 to 2 facts (cite sources in the description).
- 0:40 to 2:10 live demo on a phone screen: snap photo, medicines appear, switch to Hindi, read aloud, schedule + reminder, cheaper generic found.
- 2:10 to 2:40 how it works (simple architecture), accuracy result, privacy.
- 2:40 to 3:00 impact + what's next.
- Screen recording (free: OBS or the browser), voiceover by Abhijeet or a free TTS voice, no copyrighted music, captions on. Upload to YouTube (unlisted or public).

## What Abhijeet does
- Join DSH Hacks V2 on Devpost with his real name.
- Create a free Gemini API key and save it in Hark-Two's secure form.
- Approve making the `parchi` repo public; connect Vercel/Appwrite if needed.
- Provide or approve 3 to 5 sample prescription photos with names/phone numbers covered.
- Record the voiceover (or approve TTS), watch the final video, press Submit.

## Rules for this project
- Never store real patient data. Blur/remove personal info from samples.
- Always show "This is not medical advice. Confirm with your doctor or pharmacist."
- No secrets in the repo. Commits as Abhijeet's account via the token.

## Done
## Doing next
- Read rules/resources, confirm new project OK, start skeleton.
## Blocked
## Questions for Abhijeet
