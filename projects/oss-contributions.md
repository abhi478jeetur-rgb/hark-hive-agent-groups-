# Open-source contributions — issue scouting (owner: Hark-Two)

Goal: find easy, real open-source issues Abhijeet (GitHub `abhi478jeetur-rgb`) can claim and finish fast, so he gets merged contributions. Hark drafts the work; Abhijeet reviews and posts comments/PRs himself (Hark's GitHub app can't comment or fork on other people's repos).

## Filters (must all hold)
- Repo has **100+ stars**, pushed in the last 7 days, accepts outside PRs (read CONTRIBUTING.md; skip repos that say they don't accept external PRs, e.g. Formbricks, Documenso).
- Issue is **open and unassigned**, ideally 0-1 comments, and nobody in the comments has claimed it or opened a linked PR.
- Small and clear: docs, translations (Hindi is his strength), typos, small UI/bug fixes in TypeScript/React. Labels like `good first issue`, `help wanted`, `documentation`.

## Token budget (important)
- Keep it cheap: a few targeted `search_issues` queries (e.g. `is:issue is:open no:assignee label:"good first issue" created:>2026-10-15`), then `repo_get` only on candidates to check stars. Don't clone repos. Stop at **5 good picks**.
- Don't repeat ones already used: Drix10/ai-resources #33 #34, Translate-It-App/Translate-It #394, cxlinux-ai/cx-core #787, getsotto/sotto #758, sarmadiq9090-coder/Remember-Me #57, bschlaack/Orynivo #181, KrunalPanchal1995/pan-iit-oss #141.

## Deliverable
Create `projects/oss-picks-YYYY-MM-DD.md` with, for each pick:
1. Repo, stars, issue link, one line on the task (Hinglish is fine).
2. Why the chance is high (fast maintainer, clear acceptance criteria, etc.).
3. The exact claim comment Abhijeet should paste (short, friendly, human English, says what he'll do; mention native Hindi speaker only for Hindi tasks).
Then post an UPDATE on BOARD.md (To: Hark-One) with the file path. Deadline: within 1 hour of reading this.
