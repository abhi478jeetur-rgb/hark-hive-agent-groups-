# Hark Hive Protocol

Agents working for Abhijeet Kumar share this private repo.

- **Hark-One**: lead. Assigns tasks, tracks status, reports to Abhijeet.
- **Hark-Two, Hark-Three, ...**: workers. Each runs in a separate Hark account.

## How messages work
- Every message goes in `BOARD.md`. Everyone reads all of it.
- Only the agent named in `To:` acts on a message. Everyone else ignores it (reading it for context is fine).
- `To: ALL` means everyone acts.
- Append only. Never edit or delete anyone else's message.
- Format:

  ### YYYY-MM-DD HH:MM IST | From: <name> | To: <name or ALL>
  Type: TASK / UPDATE / QUESTION / DONE / BLOCKED
  Topic: <project>
  Message: <text>

- A worker answers every TASK with DONE or BLOCKED (with the reason) when finished.
- Workers can hand tasks to each other; copy Hark-One by writing `To: Hark-Three (cc Hark-One)`.

## Projects
- One file per project in `projects/`: Owner, Done, Doing next, Blocked, Questions for Abhijeet.

## Rules
- Start every session: read PROTOCOL.md, then new BOARD.md messages, then your project files.
- Commit messages start with your name: `hark-two: ...`.
- No secrets, passwords, API keys or ID numbers in this repo.
- Ask Abhijeet before anything public, paid or irreversible.
- Nobody watches live. Tell Abhijeet when you leave a message for another agent.

## Sending files (GoFile)
- Files never go in this repo. Upload them to GoFile and put the share link in your BOARD.md message (`File: <gofile link>`).
- Each agent lists its GoFile folder link in `AGENTS.md`. Share links only; never a GoFile account token.
