# Pick a Bounty

Do this before you open an editor. A wrong pick costs the whole weekend.

> If you couldn't win it without AI, AI won't make you win it.

AI speeds up building. It doesn't supply judgment — and choosing a bounty, spotting the real difficulty, and knowing whether the output is right are all judgment. Pick where you have domain feel.

## 1. Collect

For every bounty: the brief, the judging rubric, the prize, and any data or APIs provided.

## 2. Research

Run a deep research pass on each brief (`prompts/01-research-bounties.md`). You want: who the sponsor is, what they actually care about, what already exists, and where the hard part is.

## 3. Check the data exists

For each data source the bounty needs:

| Source | Public API? | Auth / key | Rate limits | Sample call worked? |
|--------|-------------|------------|-------------|---------------------|
|        |             |            |             |                     |

If the data isn't reachable through an API or a provided file, the bounty is secretly a scraping project. Skip it or budget your first day for it.

## 4. Score against your real skills

Score 1–5. Be honest — score what you know, not what you wish you knew.

| Bounty | Domain feel | Stack fit | Data exists | Hard part is clear | Rubric fits your strengths | Total |
|--------|-------------|-----------|-------------|--------------------|----------------------------|-------|
|        |             |           |             |                    |                            |       |

## 5. Name the hard part

Write one sentence: "The hard part of this bounty is ___." If you can't, you don't understand it yet. (Example: translating plain English into government funding taxonomy — not building a search box.)

## Red flags

- Picking for clout or the biggest prize
- A domain you have no feel for — the sponsor lives in it and will spot subtle mistakes in thirty seconds
- Data that needs scraping
- A rubric weighted toward something you can't show in a five-minute demo

## Decision

Copy the winner's brief and rubric into `brief/brief.md`.
