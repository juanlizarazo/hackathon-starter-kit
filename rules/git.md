# Git & Pull Request Rules

## Commits

**Commit Format** `[GIT-01]`:
- Use conventional commits format: `type: description`
- Types: `feat`, `fix`, `refactor`, `docs`, `test`, `style`, `chore`
- Concise messages focusing on "why" not "what"

## Pull Requests

**Pull Request Format** `[GIT-02]`:
- Title: Use conventional commits format
  - Example: `feat: add founder navigator AI chat`
- Body: Use this template:
  ```markdown
  ## Changes
  - Bullet point list of main changes

  ## Testing
  - [ ] Step-by-step checklist of what to open, click, and verify
  - [ ] Cover the happy path, edge cases, and any related existing features that could regress
  - [ ] One checkbox per verifiable action (not per feature)
  ```
- `[GIT-03]` When updating an existing PR description, **never overwrite already-checked testing items** (`- [x]`). Preserve all checked boxes and only append new unchecked items for changes added since the last update.

## Workflow

- `[GIT-04]` Only commit or push when explicitly asked. After a code change, stop and wait.
- `[GIT-05]` Never add `Co-Authored-By` trailers or "Generated with" attribution to commits or PR descriptions.
