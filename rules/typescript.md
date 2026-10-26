# TypeScript, Comments, Packages & Error Handling Rules

## Comments

- `[CMT-01]` Do NOT add comments to TypeScript code
- `[CMT-02]` Code should be self-documenting with clear variable/function names
- `[CMT-03]` HTML template comments are acceptable for section organization
- `[CMT-04]` Exception: Complex regex or algorithms may have a brief explanation

## TypeScript Conventions

- `[TS-01]` Use descriptive, human-friendly names for all identifiers — variables, parameters, properties, and functions must clearly communicate intent. No single-letter or cryptic names (e.g., use `subscription` not `s`, `error` not `e`, `value` not `v`, `user` not `u`). Exception: conventional loop counters (`i`, `j`) in simple numeric `for` loops.
- `[TS-02]` Use strict typing everywhere — no `any` unless absolutely necessary. Explicit type annotations are required when the type cannot be inferred (e.g., function parameters, uninitialized variables). When a value is initialized inline, TypeScript inference is sufficient — do not add redundant type annotations (e.g., `private _flag = false` not `private _flag: boolean = false`)
- `[TS-03]` Always include visibility modifiers on methods (`public`, `private`, `protected`)
- `[TS-04]` Always include explicit return types on methods (`:void`, `:Promise<T>`, etc.)
- `[TS-05]` Always use braces `{}` for control flow blocks (no single-line `if` without braces)
- `[TS-06]` Add blank line before `return` statements, unless the method body is a single statement
- `[TS-07]` Add blank line before `if`/`for`/`while` blocks
- `[TS-08]` Prefer `interface` over `type` when possible
- `[TS-09]` Use `type` only for unions, intersections, or mapped types
- `[TS-10]` Interface names must start with `I` (e.g., `IUser`, `IOrder`, `IMetric`)
- `[TS-11]` Interfaces go in `.interfaces.ts` files
- `[TS-12]` Types go in `.types.ts` files (derived types from const objects go here, not in `.constants.ts`)
- `[TS-13]` Constants go in `.constants.ts` files (only const objects, no type exports)
- `[TS-14]` Helper/utility functions go in `.helper.ts` files — pure functions, `static` methods, never read from a database
- `[TS-15]` Services go in `.service.ts` files — instantiated classes, no `static` methods. Anything that reads or writes a database is a service
- `[TS-16]` Use `private readonly` for injected services
- `[TS-17]` Use `inject()` function instead of constructor injection
- `[TS-18]` Prefix private properties with underscore: `private readonly _myService`
- `[TS-19]` Const lookup objects use **camelCase names** with **UPPER_CASE keys** (e.g., `orderStatuses.DELIVERED`, `tourIds.ONBOARDING`). Do NOT use ALL_CAPS for the object name itself.

## Package Management

- `[PKG-01]` Use `--exact` flag when installing packages (no `~` or `^` in versions)
  - Example: `yarn add --exact package-name`
- `[PKG-02]` Use **yarn** as the package manager (not npm). Use `yarn` for installs and `yarn run` for scripts.

## Error Handling

- `[ERR-01]` Backend: Parse API errors and return user-friendly messages
- `[ERR-02]` Frontend: Display errors using `AlertBannerComponent`
- `[ERR-03]` Log errors to console for debugging

## File Organization

```
app/src/app/
├── core/                    # Core services, guards, interceptors
│   └── services/
├── shared/                  # Shared components, layouts, forms
│   ├── components/
│   ├── layouts/
│   └── forms/
├── [feature]/              # Feature modules
│   ├── services/
│   ├── [component]/
│   └── [feature].routes.ts
functions/src/
├── [feature]/
│   ├── functions/          # Cloud functions
│   └── services/           # Business logic services
├── constants.ts
└── index.ts                # Function exports
```

## Shared Types Pattern

Types are shared between frontend and backend using local virtual npm packages:
- `functions/lib/firestore/index.d.ts` - Firestore document interfaces (backend)
- `functions/lib/types/index.d.ts` - API contract types (callables request/response)
- `app/src/types/firestore.d.ts` - Firestore document interfaces (frontend, uses Firebase Timestamp)

When adding new Firestore collections:
1. Add interface to `functions/lib/firestore/index.d.ts` (uses `@google-cloud/firestore` types)
2. Add matching interface to `app/src/types/firestore.d.ts` (uses `firebase.firestore.Timestamp`)
3. Use namespace pattern: `[ProductName].Firestore.[Feature].I[InterfaceName]`

Example:
```typescript
namespace ProductName.Firestore.User {
  export interface IUserProfile {
    id?: string;
    email: string;
    createdAt: Timestamp;
  }
}
```
