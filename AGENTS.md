# AGENTS.md - Claude Code Configuration

## Project Overview

<!-- Replace this section at kickoff. Keep it to a few lines — details live in brief/. -->

**[Product Name]** is an Angular 21+ (standalone components), Angular Material, SCSS application backed by Firebase Cloud Functions (TypeScript) and Firestore, built for **[Hackathon Name]**.

**Key file:** `brief/brief.md` — challenge, judging rubric, required features, demo script. Read it before touching any feature.

---

## Hackathon Mode

This is a hackathon build. Ship the demo, not the test suite. Read `rules/hackathon.md` first — it overrides any stricter rule elsewhere.

---

## Rule Files

Rules use the format `[CATEGORY-##]`. **Read only the files relevant to your task** — do not load all of them.

| File | Categories | Load when… |
|------|-----------|------------|
| `rules/hackathon.md` | HACK | Always — scope, speed, testing stance |
| `rules/typescript.md` | CMT, TS, PKG, ERR, file organization, shared types | Any TypeScript work |
| `rules/angular.md` | ANG, MAT | Frontend components or templates |
| `rules/scss.md` | SCSS, theme variables | Styling work |
| `rules/ui.md` | UI, cards, page headers, forms, side panels | UI components or patterns |
| `rules/firebase.md` | FB | Cloud Functions or Firestore |
| `rules/git.md` | GIT | Commits or PRs |

**Example**: a Cloud Function task → read `rules/hackathon.md` + `rules/typescript.md` + `rules/firebase.md`. Skip the rest.

---

## Agent Workflow

- `[AGT-01]` Do NOT use the `superpowers:subagent-driven-development` skill — it's too slow for a hackathon clock. Implement plans directly.
- `[AGT-02]` DO use subagents to parallelize independent work (e.g., backend function + frontend screen, or research while building). Use `superpowers:dispatching-parallel-agents` or the Agent tool directly.
- `[AGT-03]` Use `superpowers:brainstorming` for scoping a new feature, and `superpowers:systematic-debugging` for bugs. Skip `superpowers:test-driven-development` (see `[HACK-06]`).
- `[AGT-04]` Keep plans short — a checklist in chat, not a multi-page plan document.

---

## Universal Rules

- Always include a newline at the end of files
- Do NOT add comments to TypeScript code (`[CMT-01]`) — code should be self-documenting
- Only commit or push when explicitly asked (`[GIT-04]`)
