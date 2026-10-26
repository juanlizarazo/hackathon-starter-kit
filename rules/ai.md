# AI Rules

AI is a component, not the architecture. The model sits at the edges of the system, never in the middle.

## Where AI Goes

- `[AI-01]` Use a model for **unstructured input → structured data**: a sentence becomes attributes, a messy document becomes field values.
- `[AI-02]` Use a model for **structured data → unstructured output**: the explanation of a result, a summary, a draft message.
- `[AI-03]` Deterministic logic is code: scoring, eligibility, filters, ranking, math, validation. No model in that path.
- `[AI-04]` Structured work uses libraries: parsing, date math, generating files, filling a PDF form (`pdf-lib`). A model may read the messy source and hand back values; code writes them.
- `[AI-05]` The model makes no decisions. It adapts input and explains output; rules decide.
- `[AI-06]` The test: unstructured in, structured out → model. Already structured → code.

```
Sentence → [AI] → Structured attributes → Rules engine → Match → [AI] → Explanation
```

## Implementation

- `[AI-07]` Give every AI input path a non-AI equivalent where it's cheap (e.g., a guided form and a "describe instead" box that feed the same engine).
- `[AI-08]` Request JSON output and validate it against a TypeScript interface before use. On invalid output, retry once, then fail with a human-friendly error.
- `[AI-09]` Call models from Cloud Functions, never from the client. API keys live in Firebase secrets (`[FB-05]`).
- `[AI-10]` Keep prompt text in `.constants.ts` files (`[TS-13]`), not inline in business logic.
- `[AI-11]` Cache or seed AI results on the demo path so a slow or failed call can't break the demo.
