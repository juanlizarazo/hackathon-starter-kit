# Hackathon Starter Kit

Agent rules and a brief template for building hackathon projects fast with Claude Code (or any agent that reads `AGENTS.md`).

**Built for Angular.** The rules target **Angular 21+ (standalone) · Angular Material · SCSS · Firebase Cloud Functions · Firestore**.

> **Using a different framework?** Keep `rules/hackathon.md`, `rules/git.md`, the agent workflow in `AGENTS.md`, and the brief template — those are framework-agnostic. Then rewrite or replace `angular.md`, `scss.md`, `ui.md`, and `firebase.md` for your stack (e.g., `react.md`, `tailwind.md`, `supabase.md`), adjust `typescript.md` as needed, and update the rule-file table in `AGENTS.md` to match.

## Why it's split

One giant `AGENTS.md` eats context on every turn. Here `AGENTS.md` is a short index, and the detailed rules live in `rules/`. The agent loads only the files that matter for the task at hand.

```
.
├── AGENTS.md          # Index: project overview, rule-file table, universal rules
├── CLAUDE.md          # Points Claude Code at AGENTS.md
├── .claude/settings.json  # Enables the plugins below for everyone who clones
├── brief/
│   └── brief.md       # Fill in at kickoff: problem, rubric, scope, demo script
└── rules/
    ├── hackathon.md   # HACK — scope, speed, no detailed unit tests, demo polish
    ├── typescript.md  # CMT, TS, PKG, ERR, file organization, shared types
    ├── angular.md     # ANG, MAT
    ├── scss.md        # SCSS, theme variables
    ├── ui.md          # UI — cards, page headers, forms, side panels
    ├── firebase.md    # FB — Cloud Functions
    └── git.md         # GIT — commits, PRs
```

## Use it

1. Copy `AGENTS.md`, `CLAUDE.md`, `.claude/settings.json`, `rules/`, and `brief/` into your new project (or use this repo as a GitHub template).
2. Fill in the **Project Overview** in `AGENTS.md` (a few lines only).
3. Fill in `brief/brief.md` with the challenge, judging rubric, and demo script.
4. Make the per-project swaps:
   - `rules/typescript.md` — Firestore namespace (`ProductName.Firestore...`)
   - `rules/ui.md` — global class prefix (`app-`)
   - `rules/scss.md` — theme colors
5. Delete rule files you won't use (e.g., `firebase.md` for a frontend-only build) and remove their rows from the table in `AGENTS.md`.

## Claude Code plugins & skills

`.claude/settings.json` enables these plugins from the official marketplace (`anthropics/claude-plugins-official`), so Claude Code offers to install them when you open the repo:

| Plugin | What it's for |
|--------|---------------|
| `superpowers` | Process skills — brainstorming, systematic debugging, parallel agents, verification before claiming done |
| `frontend-design` | Distinctive UI that doesn't look like a template — matters for the demo |
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
- **Skip:** `superpowers:test-driven-development` — no detailed unit tests during a hackathon (`[HACK-06]`).

## Stack variants

- **Tailwind instead of Material/SCSS**: drop `scss.md` and the `MAT` section, then add your Tailwind conventions as `rules/tailwind.md`.
- **Signals**: flip `[ANG-03]` in `rules/angular.md` to "Use signals for reactive state (`signal()`, `computed()`, `effect()`)".

## Adding rules

- Use the `[CATEGORY-##]` format so rules can be referenced in reviews ("violates `[TS-05]`").
- Put a new category in its own file and add a row to the table in `AGENTS.md` saying when to load it.
- Keep `AGENTS.md` itself short. If something only applies to some tasks, it belongs in `rules/`.
