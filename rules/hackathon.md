# Hackathon Rules

These rules win over any stricter rule in other files. This is not production code.

## Scope

- `[HACK-01]` Read the judging rubric before the brief. The rubric weights decide where hours go — design and usability often outweigh technical execution.
- `[HACK-02]` The brief is the spec, not a floor. Take its constraints literally (e.g., "leads to verify, not confirmed eligibility") — they exist to cut work. Never build what the brief says not to.
- `[HACK-03]` If a feature doesn't move a rubric criterion or the demo, skip it. A five-minute demo fits a handful of features, not eleven.
- `[HACK-04]` Build the demo path end-to-end first, then widen. A thin working flow beats a half-built broad one.
- `[HACK-05]` Prefer the simplest thing that demos well. No premature abstractions, no generic frameworks, no config systems.
- `[HACK-06]` Hardcode or seed data when real integrations would eat the clock. Make the seam obvious so it can be swapped later.
- `[HACK-07]` When a scoping call is ambiguous, ask — don't silently build the bigger version.

## Testing

- `[HACK-08]` Don't write tests for coverage. No full test suites, no spec file per component or service.
- `[HACK-09]` Keep tests that already exist, including ones written to validate an implementation. Don't delete or rewrite working specs.
- `[HACK-10]` A small focused test is fine for tricky pure logic (scoring, parsing, date math) when it's faster than checking by hand.
- `[HACK-11]` Verify by running the app and walking the demo path. Report what you clicked and what you saw.

## Code Quality (still matters)

- `[HACK-12]` Speed is not an excuse for unreadable code. Naming, typing, and file organization rules still apply — judges and teammates read the code.
- `[HACK-13]` No secrets in the repo. Use Firebase secrets or `.env` files that are gitignored.
- `[HACK-14]` Keep the app deployable at all times — the demo may be pulled live at any moment.

## Demo Polish

- `[HACK-15]` Every screen on the demo path needs a loading state, an empty state, and a human-friendly error.
- `[HACK-16]` Mobile must not look broken — judges open links on phones.
- `[HACK-17]` Seed realistic demo data (real-sounding names, plausible numbers). No "test test" or lorem ipsum on the demo path.
- `[HACK-18]` Keep `README.md` current: pitch, live link, demo flow (step-by-step), and any demo shortcuts (e.g., admin login).

## Last Mile

The hours saved by cutting scope go here. This is where projects win.

- `[HACK-19]` Once it works, audit the build against the brief in a fresh session, scoring each requirement as a percentage (`prompts/05-audit.md`).
- `[HACK-20]` Run persona reviews — staff architect, UX lead, the sponsor (`prompts/06-persona-review.md`).
- `[HACK-21]` Reserve two to three hours for UI refinement after the demo path works (`prompts/07-ui-polish.md`).
- `[HACK-22]` Ship a live URL the judge can touch. Not a video, not slides.
