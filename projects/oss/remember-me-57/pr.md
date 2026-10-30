# Title
i18n(hi): polish awkward Hindi strings

# Body
## What changed

Part of #57. Hindi (`ui/locales/hi.json`) only, values only, no keys changed. 26 entries fixed where the wording was formal, stiff, inconsistent or ambiguous:

- "Dismiss" was "हटाएँ", the same word as Delete; now "ख़ारिज करें".
- Restart now uses "रीस्टार्ट" everywhere, so it no longer looks like Resume ("फिर शुरू").
- Everyday tech words instead of formal ones where the file already used them elsewhere: एक्सपोर्ट, लोकल, पाथ, सॉर्ट, कॉमा.
- "अप्रयुक्त" → "बिना इस्तेमाल वाले", "नियत" → "समय", "{duration} से देर" → "{duration} की देरी", "Reschedule…" → "समय बदलें…".

All `{placeholders}` and plural forms kept, digits are 0-9. Language: Hindi. I'm a native Hindi speaker. I used an AI assistant to draft the edits and reviewed every string myself.

## Validation

- [x] `pnpm test` passes (201 tests)
- [x] `node tools/i18n-keys.cjs`: hi 0 missing
- [ ] Arabic RTL interface checked (not touched)
- [ ] English LTR interface checked (not touched)
- [x] No user data, attachments, backups, or generated release files included

I did not run the app on Windows, so the changed text was not checked in the UI.
