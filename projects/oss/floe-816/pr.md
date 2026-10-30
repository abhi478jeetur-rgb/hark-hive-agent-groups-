# Title
fix(client): the home page names the browser among receivers that confirm delivery

# Body
Closes #816

- `CapabilitiesSection.tsx`: the last sentence of the "Checked on arrival" tile now reads "Browser, CLI, and Floe Desktop receivers confirm delivery." Nothing else on the page changes.
- `client/lib/capabilitiesText.test.ts`: the test from the issue, pinning that sentence beside `RECEIVER_CONFIRMS`. It fails on `main` and passes with this change.
- `docs/changelog.mdx`: a "Web app:" bullet under Unreleased, and "Web" added to that entry's tags after "Desktop".

Checks run: in `client/`, `pnpm install --frozen-lockfile`, `pnpm lint`, `pnpm test` (103 files, 1520 passed), `node scripts/check-titles.mjs`; from the root, `check-consumers.mjs` and `docs-check.mjs all` (0 hard). I did not run `pnpm build` or the two `node --test` globs locally.

Note: I used an AI assistant to help with this change and reviewed it myself.
