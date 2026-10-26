# Hackathon Starter Kit

Agent rules, prompts, and templates for building winning hackathon projects fast with Claude Code (or any agent that reads `AGENTS.md`).

**Built for Angular.** The rules target **Angular 21+ (standalone) · Angular Material · SCSS · Firebase Cloud Functions · Firestore**.

> **Using a different framework?** Keep `rules/hackathon.md`, `rules/ai.md`, `rules/git.md`, the agent workflow in `AGENTS.md`, the prompts, and the templates — those are framework-agnostic. Then rewrite or replace `angular.md`, `scss.md`, `ui.md`, and `firebase.md` for your stack (e.g., `react.md`, `tailwind.md`, `supabase.md`), adjust `typescript.md` as needed, and update the rule-file table in `AGENTS.md` to match.

## Use it tonight

1. Click **Use this template** (or copy the files into your project).
2. Pick your bounty with `brief/pick-a-bounty.md`.
3. Fill in `brief/brief.md` and the **Project Overview** in `AGENTS.md`.
4. Follow the prompts in `prompts/` in order.

## Day 0 — before the clock starts

Everything here costs zero hackathon hours if you do it beforehand.

- [ ] This kit, with the per-project swaps below done
- [ ] A hosting account, live and deployable (Firebase Hosting, Vercel)
- [ ] A database you never think about (Firestore)
- [ ] An email API key (Resend, Mailgun) — a real email landing beats a mockup
- [ ] An AI orchestrator with two providers connected (e.g., Conductor with Claude Code + Codex), so you can switch when you hit a limit
- [ ] Your model API keys, with credits

Tokens are a budget. Small sessions with less context burn fewer of them.

## The workflow

| Step | What | Where |
|------|------|-------|
| 1 | Read the rubric, research every brief, pick one | `brief/pick-a-bounty.md`, `prompts/01-research-bounties.md` |
| 2 | Fill in the brief | `brief/brief.md` |
| 3 | General plan: phases built to run in parallel, blocking work first | `plans/00-general.md`, `prompts/02-general-plan.md` |
| 4 | Per phase, in a new session: plan, build, skim, commit, PR | `plans/phase-template.md`, `prompts/03-phase-plan.md`, `prompts/04-parallel-phases.md` |
| 5 | Last mile: audit, persona reviews, UI polish with the `frontend-design` plugin, mobile, live URL | `prompts/05-audit.md`, `prompts/06-persona-review.md`, `prompts/07-ui-polish.md` |

What it skips on purpose: subagent-driven development, test suites written for coverage, full code reviews, and cosmetic fixes. Polish what the judge sees, not what the judge might read.

> **If you're new to coding,** skim less and read more. Skimming AI output works when you can tell it's wrong. That's the one corner not to cut.

## Why it's split

One giant `AGENTS.md` eats context on every turn. Here `AGENTS.md` is a short index, and the detailed rules live in `rules/`. The agent loads only the files that matter for the task at hand.

```
.
├── AGENTS.md              # Index: overview, rule-file table, agent workflow, universal rules
├── CLAUDE.md              # Points Claude Code at AGENTS.md
├── .claude/settings.json  # Enables the plugins below for everyone who clones
├── brief/
│   ├── pick-a-bounty.md   # Research, data check, skill scoring, red flags
│   └── brief.md           # Fill in at kickoff: problem, rubric, scope, demo script
├── plans/
│   ├── 00-general.md      # Phases, parallelism, blocking work, requirements list
│   └── phase-template.md  # Copy per phase
├── prompts/               # Sample prompts for each step, in order
└── rules/
    ├── hackathon.md       # HACK — scope, testing stance, demo polish, last mile
    ├── ai.md              # AI — AI is a component, not the architecture
    ├── typescript.md      # CMT, TS, PKG, ERR, file organization, shared types
    ├── angular.md         # ANG, MAT
    ├── scss.md            # SCSS, theme variables
    ├── ui.md              # UI — cards, page headers, forms, side panels
    ├── firebase.md        # FB — Cloud Functions
    └── git.md             # GIT — commits, PRs
```

## Per-project swaps

- `AGENTS.md` — Project Overview (a few lines only)
- `rules/typescript.md` — Firestore namespace (`ProductName.Firestore...`)
- `rules/ui.md` — global class prefix (`app-`)
- `rules/scss.md` — theme colors
- Delete rule files you won't use (e.g., `firebase.md` for a frontend-only build) and remove their rows from the table in `AGENTS.md`.

## Claude Code plugins & skills

`.claude/settings.json` enables these plugins from the official marketplace (`anthropics/claude-plugins-official`), so Claude Code offers to install them when you open the repo. These are the plugins I use on every hackathon build:

| Plugin | What it's for |
|--------|---------------|
| `superpowers` | Process skills for the whole build — brainstorming, systematic debugging, parallel agents, verification before claiming done |
| `frontend-design` | The UI refinement pass — two to three hours after the demo path works, so it doesn't look like a template (`prompts/07-ui-polish.md`) |
| `code-review` | Quick review pass before merging or pitching |

Install manually if needed:

```
/plugin install superpowers@claude-plugins-official
/plugin install frontend-design@claude-plugins-official
/plugin install code-review@claude-plugins-official
```

### How the agent should use them (enforced in `AGENTS.md` → `[AGT-##]`)

- **Use:** `superpowers:brainstorming` to scope features, `superpowers:systematic-debugging` for bugs, `superpowers:dispatching-parallel-agents` to split independent work across subagents, `superpowers:verification-before-completion` before saying something works.
- **Don't use:** `superpowers:subagent-driven-development` — it reviews every task with extra agents and takes much longer. Subagents are for parallelism, not ceremony.
- **Skip:** `superpowers:test-driven-development` — no tests written for coverage during a hackathon (`[HACK-08]`). Tests that already exist stay.

## Stack variants

- **Tailwind instead of Material/SCSS**: drop `scss.md` and the `MAT` section, then add your Tailwind conventions as `rules/tailwind.md`.
- **Signals**: flip `[ANG-03]` in `rules/angular.md` to "Use signals for reactive state (`signal()`, `computed()`, `effect()`)".

## Adding rules

- Use the `[CATEGORY-##]` format so rules can be referenced in reviews ("violates `[TS-05]`").
- Put a new category in its own file and add a row to the table in `AGENTS.md` saying when to load it.
- Keep `AGENTS.md` itself short. If something only applies to some tasks, it belongs in `rules/`.

## Say hi

Used the kit? Tell me how it went or ask questions on Instagram: [instagram.com/juaninvests](https://instagram.com/juaninvests)
