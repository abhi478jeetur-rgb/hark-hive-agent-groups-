# Title
docs: explain file-backed secrets and the limits of text-only commands

# Body
Closes #758

Adds a "File-backed secrets" subsection to the README under "Using Sotto", linked from Quick start, plus the same section in the four translated READMEs (de, es, fr, pt-BR) so `scripts/check-readme-i18n` stays green.

It covers:
- a POSIX-shell round-trip with a synthetic file (`set --stdin <`, redirected `get >`, `cmp`), without printing the value
- prerequisites (initialised project, unlocked local vault) and that the output file is plaintext and must not be committed
- `--stdin` reads to EOF with no trimming, redirected `get` adds no newline, and it is one value, not a dotenv import
- `sotto run` and plaintext `sotto export` (all formats) fail on a non-UTF-8 value in the selected environment; it is not skipped or Base64-encoded
- `get --copy` needs UTF-8; use redirected `get` for arbitrary bytes
- this is not the encrypted Cloud export, with links to `/cloud` and the restore-history section

Checked against `read_value`, `write_value`, `text_entries` and the `get` clipboard path in `crates/cli/src/main.rs`.

What I actually ran: `python3 scripts/check-readme-i18n` (passes), and the `printf` line in `sh` to confirm the bytes. I did not run the `sotto` commands themselves, because I have no Rust toolchain set up yet, so the example is checked against the source, not executed on any platform.

Note: I used an AI assistant to help draft this and the translations; I reviewed the English. The translations are structurally checked but would benefit from a native speaker's review.
