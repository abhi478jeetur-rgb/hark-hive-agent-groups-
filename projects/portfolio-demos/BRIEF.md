# Portfolio Demos — 10 animated landing pages (Owner: Hark-Two)

Requested by Abhijeet on 2026-11-04 20:32 IST. Lead: Hark-One. Worker: Hark-Two.

## Goal
Build about **10 animated demo landing pages**, deploy each on **Vercel**, and add each one to the **gallery** of Abhijeet's live portfolio, with a tiny animated preview. Everything should look like Abhijeet made it.

## Before you start
- Look online for good **skills/playbooks** that raise design and animation quality (for example Anthropic's frontend-design skill, GSAP/Three.js/Lenis animation guides). Load and use them.
- Tokens: Abhijeet will give you his **GitHub token** and a **Vercel token** through your Hark vault/secure form. Never put any token in chat, code, commits, logs or this repo.

## Sources for ideas
1. **Instagram reels**: https://www.instagram.com/ascenta.studio/reels/ (plus more profile links Abhijeet will send you). Open each profile, pick the **2–3 most viral reels** (highest views/likes), watch them and note the website design + animation style.
   - Known blocks: the downloader sites snapinsta.app, sssinstagram.com, fastdl.app, f-d.app did not work for Hark-One. Do not rely on them; watch the reels in the browser instead.
2. **https://motionsites.ai/**: open every **free** template and copy its prompt/code. If the copy fails after 2–3 tries, clear cookies or use a fresh browser session and reopen. Check each template's licence/terms and note it.

## Rules for every demo
- **Recreate the style, not an exact copy.** Change the visuals, images, colours, copy/text and brand so it reads as our own work. A background video you can't replace may stay; replace images (and videos where possible).
- **Full landing page, minimum 3 sections.** If a prompt only covers the hero, design the rest yourself to match its theme (features, showcase, CTA/footer etc.).
- **Animation quality high everywhere**: scroll reveals, hover states, smooth scrolling, particles. **3D = write it yourself in Three.js** (no AI-generated video standing in for 3D).
- Ideas worth using: particles.casberry.in (AI particle generator, exports Three.js code), Origin UI (coss.com/origin, MIT React+Tailwind components), daisyUI (daisyui.com, Tailwind themes).
- **Top label "Mera Portfolio"** on every demo: a small fixed pill/button that goes back to https://abhijeet-portfolio-orpin.vercel.app/gallery.html .
- **Social links on every demo** (footer or floating):
  - Instagram https://www.instagram.com/abhi.jeetkuumar/
  - GitHub https://github.com/abhi478jeetur-rgb
  - LinkedIn https://www.linkedin.com/in/abhijeet-kumar-4b6a083b0/
  - X https://x.com/Abhijeetkuumar
  - YouTube https://www.youtube.com/@AbhijeetKumarz7r
  - Peerlist https://peerlist.io/abhijeetkuumar
  - Freelancer https://www.freelancer.com/u/abhijeetk371
  - WhatsApp https://wa.me/919430322551
- **Interlink all demos** ("More demos" strip linking the other demos).
- **No location anywhere** (no city/state/country, no geo meta). **No hackathon mentions.** Say "Graphic Designing", never "Thumbnails".
- Mobile-first, fast (lazy-load media, compress images to webp), Lighthouse sanity check.

## Deploy
- One Vercel project per demo (or one repo per demo under abhi478jeetur-rgb, auto-deployed). Use the Vercel token from the vault.
- Ask Abhijeet before making anything public that he hasn't seen, if in doubt.

## Add to the portfolio gallery
- Repo: https://github.com/abhi478jeetur-rgb/abhijeet-portfolio (Vercel auto-deploys `main` in ~1 min to https://abhijeet-portfolio-orpin.vercel.app/).
- **Your file only: `gallery/web.js`** (`window.GALLERY_WEB = [ ... ]`). Hark-One edits `gallery/design.js` for designs/videos. Never rewrite the whole repo tree; update single files with the GitHub contents API (`PUT /repos/.../contents/<path>` with the current file `sha`) so you don't overwrite Hark-One's commits. Pull latest before every change.
- Item shape (newest first):
  ```js
  { title: "Nova Studio", category: "Websites", /* or "3D Websites" */ year: "2026",
    preview: "assets/gallery/nova.webp",   // ~1200x750 webp poster
    video:   "assets/gallery/nova.webm",   // small muted loop
    link:    "https://nova-demo.vercel.app" }
  ```
- **Preview loop must be tiny**: 3–5 s, ~640px wide, WebM/VP9 (or animated webp), target **< 300 KB**; strip metadata (`ffmpeg -map_metadata -1 -an`). Record with Playwright + ffmpeg.
- Filters already in the site: All, AI Video, Video Editing, Motion Graphics, Graphic Designing, 3D Websites, Websites, Apps.

## Gallery behaviour to build (engine: script.js + style.css)
- **Mobile**: clicking a demo opens it **in the same tab** inside a full-screen viewer with a short Shorts-style swipe/landing animation (iframe or page transition); back button / swipe returns to the gallery. No new tab.
- **Desktop**: opens in a **new tab** (`target="_blank" rel="noopener"`).
- Keep all existing animations (agent builders, Thanos theme snap, dark red/black + light sunflower themes). Touch only what this needs.

## How Hark-One worked (experience)
- Portfolio source is plain HTML/CSS/JS + GSAP (no framework). Content in `config.js`; theme colours top of `style.css`; engine `script.js`.
- After content changes run `node tools/seo-files.js` and `node tools/prerender.js` (bakes text for crawlers). OG images: `node tools/og/render.js` (Playwright), then bump `?v=` in the HTML.
- `git push` over https failed in Hark-One's sandbox; the GitHub REST git-data API (blobs → tree → commit → update ref) worked. Prefer per-file contents API now.
- Scores now: desktop Lighthouse 96/97/100/100, mobile performance 74. Don't make the gallery heavier: lazy-load previews, play loops only in view.
- Known unfixed issues: dark hero stats overlap the red "O" slightly; intro size labels white-on-blue contrast.
- Deliver files to Abhijeet via **GoFile** links. Never synthesize music/SFX for videos; use licensed library assets only.

## Status
- Done: brief written; gallery data split into `gallery/web.js` + `gallery/design.js` (commit 1ad71a7).
- Doing next (Hark-Two): skills → reels study → motionsites prompts → demo 1.
- Blocked: needs GitHub + Vercel tokens in Hark-Two's vault, and Abhijeet's extra Instagram links.
- Questions for Abhijeet: none yet.
