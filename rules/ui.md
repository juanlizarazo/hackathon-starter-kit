# UI/UX Patterns

Global classes use the `app-` prefix. Rename to a short project prefix at kickoff (e.g., `ss-`, `pl-`) and keep it consistent.

## Loading States

- `[UI-01]` Use global `LoadingService` for page/data loading
- `[UI-02]` Use inline spinners for button actions (spinner only, no text while loading)
- `[UI-03]` Minimum loading time for iframes: 2 seconds

## Global Card Styles (`styles.scss`)

Use the global `app-card` classes for consistent clickable card lists:

```html
<div class="app-card-grid">
  <mat-card class="app-card app-card--clickable" appearance="outlined" routerLink="/path">
    <mat-card-content>
      <div class="app-card-header">
        <div class="app-card-icon">
          <mat-icon>icon_name</mat-icon>
        </div>
        <div class="app-card-content">
          <h4>Card Title</h4>
          <p>Card description text</p>
        </div>
        <mat-icon class="app-card-arrow">chevron_right</mat-icon>
      </div>
    </mat-card-content>
  </mat-card>
</div>
```

Note: Always use `appearance="outlined"` on mat-card for flat white cards with borders.

Classes:
- `.app-card` - Base card with border, 12px radius, white background
- `.app-card--clickable` - Adds hover effects (border color, shadow, translateY)
- `.app-card-header` - Flexbox row layout with centered items
- `.app-card-icon` - 48x48 circular icon container with primary background and white icon
- `.app-card-content` - Flex content area with h4 title and p description
- `.app-card-arrow` - Chevron arrow (gray, 24px)
- `.app-card-grid` - Container with flex column, 12px gap, max-width 600px

## Global Page Header Styles (`styles.scss`)

Use the global `app-page-header` classes for page headers with actions:

```html
<div class="app-page-header">
  <div class="app-page-header-left">
    <h1 class="app-page-title">Page Title</h1>
    <p class="app-page-subtitle">Page description or subtitle</p>
  </div>
  <button mat-flat-button class="app-page-action">
    <mat-icon>add</mat-icon>
    <span>Action</span>
  </button>
</div>
```

Classes:
- `.app-page-header` - Flexbox row with space-between, 24px bottom margin
- `.app-page-header-left` - Flex container for title/subtitle
- `.app-page-title` - Bold title (600 weight), no margins
- `.app-page-subtitle` - Gray subtitle text
- `.app-page-action` - Button container with icon styling

## Forms

- `[UI-04]` Max width `600px` for form containers on large screens
- `[UI-05]` Use `mat-hint` for field guidance
- `[UI-06]` Show validation errors inline with `mat-error`

## Side Panels / Bottom Sheets

- `[UI-07]` Use `SidePanelComponent` instead of dialogs for contextual content
- `[UI-08]` **Default behavior**: Bottom sheet (slides from bottom) — works on all screen sizes
- `[UI-09]` On desktop (>768px): Slides from right side
- `[UI-10]` On mobile (≤768px): Slides from bottom as a bottom sheet
- `[UI-11]` Max height on mobile: 85vh with border-radius on top corners

### Async Submit Pattern (form side panels)

- `[UI-12]` **Child owns the async call.** The component containing the form is responsible for calling the service and must only emit `closed` on success — never before. The parent reloads data in response to the success event; it does not do the async work itself.

- `[UI-13]` **Submit button state during save.** While saving: show a `<mat-spinner diameter="20">` in place of the button label, disable the button with `[disabled]="form.invalid || isSubmitting"`, and disable Cancel with `[disabled]="isSubmitting"`. Pass `[closable]="!isSubmitting"` to `SidePanelComponent` to prevent backdrop/X dismissal mid-save.

  ```html
  <button mat-flat-button color="primary" type="submit" [disabled]="form.invalid || isSubmitting">
    @if (isSubmitting) {
      <mat-spinner diameter="20"></mat-spinner>
    } @else {
      {{ submitLabel }}
    }
  </button>
  <button mat-button type="button" [disabled]="isSubmitting" (click)="onClose()">Cancel</button>
  ```

- `[UI-14]` **Inline error on failure.** On submit error, set a `saveError` string and display it with `<app-alert-banner>` inside the panel (above the action buttons). Do not close the panel. Clear it on the next submit attempt or on close.

  ```html
  @if (saveError) {
    <app-alert-banner [message]="saveError" (dismissed)="saveError = ''"></app-alert-banner>
  }
  ```

- `[UI-15]` **isSubmitting flag pattern.** Use a boolean flag (`isSubmitting = false`) on the component. Set it to `true` before the async call and reset it in `finally`.

  ```typescript
  public async onSubmit(): Promise<void> {
    if (this.form.invalid || this.isSubmitting) { return; }
    this.isSubmitting = true;
    try {
      await this._service.doWork(...);
      this.closed.emit();
    } catch {
      this.saveError = 'Failed to save. Please try again.';
    } finally {
      this.isSubmitting = false;
    }
  }
  ```
