# Hackathon Rules

These rules win over any stricter rule in other files.

## Scope

- `[HACK-01]` The brief (`brief/brief.md`) and its judging rubric drive every decision. If a feature doesn't move a judging criterion or the demo, skip it.
- `[HACK-02]` Build the demo path end-to-end first, then widen. A thin working flow beats a half-built broad one.
- `[HACK-03]` Prefer the simplest thing that demos well. No premature abstractions, no generic frameworks, no config systems.
- `[HACK-04]` Hardcode or seed data when real integrations would eat the clock. Make the seam obvious so it can be swapped later.
- `[HACK-05]` When a scoping call is ambiguous, ask — don't silently build the bigger version.

## Testing

- `[HACK-06]` Do NOT write detailed unit tests. No spec files for components, services, or helpers unless explicitly asked.
- `[HACK-07]` Verify by running the app and walking the demo path. Report what you clicked and what you saw.
- `[HACK-08]` Exception: a small focused test is fine for tricky pure logic (scoring, parsing, date math) when it's faster than manual checking.
- `[HACK-09]` Delete generated boilerplate specs (`*.spec.ts` with only `'should create'`) instead of maintaining them.

## Code Quality (still matters)

- `[HACK-10]` Speed is not an excuse for unreadable code. Naming, typing, and file organization rules still apply — judges and teammates read the code.
- `[HACK-11]` No secrets in the repo. Use Firebase secrets or `.env` files that are gitignored.
- `[HACK-12]` Keep the app deployable at all times — the demo may be pulled live at any moment.

## Demo Polish

- `[HACK-13]` Every screen on the demo path needs a loading state, an empty state, and a human-friendly error.
- `[HACK-14]` Mobile must not look broken — judges open links on phones.
- `[HACK-15]` Seed realistic demo data (real-sounding names, plausible numbers). No "test test" or lorem ipsum on the demo path.
- `[HACK-16]` Keep `README.md` current: pitch, live link, demo flow (step-by-step), and any demo shortcuts (e.g., admin login).
