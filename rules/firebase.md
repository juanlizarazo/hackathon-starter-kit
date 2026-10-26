# Firebase Functions Rules

## Firebase Conventions

- `[FB-01]` Use `onCall` for callable functions
- `[FB-02]` Always validate `request.auth?.uid`
- `[FB-03]` Handle errors with human-friendly messages
- `[FB-04]` Use `HttpsError` for returning errors to client
- `[FB-05]` Use Firebase secrets for sensitive values (API keys, etc.)
- `[FB-06]` Use constants in `.constants.ts` files for configuration values (avoid env vars)
- `[FB-07]` Use Firebase logger instead of `console.log`:
  ```typescript
  import * as logger from 'firebase-functions/logger';

  logger.info('Message', { key: 'value' });
  logger.error('Error message', { error: err.message, context: data });
  ```

## Adding a New Cloud Function

1. Create the function in `functions/src/[feature]/`
2. Export it from `functions/src/index.ts`
3. Add a rewrite entry in `firebase.json` under `hosting.rewrites` (before the catch-all `**` rule):
   ```json
   {
     "source": "/functionName",
     "function": "functionName"
   }
   ```
