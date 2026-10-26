# Angular & Angular Material Rules

## Angular Conventions

- `[ANG-01]` Use standalone components (no NgModules)
- `[ANG-02]` Use new control flow syntax: `@if`, `@for`, `@switch` (not `*ngIf`, `*ngFor`)
- `[ANG-03]` Do NOT use signals — use regular properties and observables
- `[ANG-04]` Component files: `.component.ts`, `.component.html`, `.component.scss`
- `[ANG-05]` Use `ScreenToolbarComponent` for page headers with back navigation
- `[ANG-06]` Use `LoadingService` for global loading state (not local progress bars)
- `[ANG-07]` Use `AlertBannerComponent` for error messages (not snackbars for errors)

If a shared component referenced above doesn't exist yet, create it in `shared/components/` the first time it's needed.

## Angular Material

- `[MAT-01]` Use Material components consistently
- `[MAT-02]` Button with icon + text pattern: wrap in a flex div for vertical alignment
  ```html
  <button mat-flat-button>
    <div class="btn-content">
      <mat-icon>icon_name</mat-icon>
      <span>Button Text</span>
    </div>
  </button>
  ```
  ```scss
  .btn-content {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  ```
- `[MAT-03]` Use `mat-flat-button` for primary actions, `mat-stroked-button` for secondary
- `[MAT-04]` Use `appearance="outline"` for form fields
