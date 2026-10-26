# SCSS & Styling Rules

## SCSS Conventions

- `[SCSS-01]` Use component-scoped styles
- `[SCSS-02]` Do NOT style native HTML elements directly (p, h1, div, etc.) — use classes instead
- `[SCSS-03]` Mobile breakpoint: `max-width: 599.98px`
- `[SCSS-04]` Tablet breakpoint: `max-width: 959.98px`
- `[SCSS-05]` Use flexbox and grid for layouts
- `[SCSS-06]` Standard border-radius: `12px` for cards, `8px` for smaller elements

## CSS Theme Variables

Use CSS variables defined in `styles.scss` for consistent theming. Swap the colors per project; keep the names.

```scss
var(--app-theme--primary, #15445b)      // Primary brand color
var(--app-theme--tertiary, #32a32f)     // Success/positive color (green)
var(--app-theme--tertiary-bg, #e8f5e9)  // Success background (light green)
var(--app-theme--accent, #d97706)       // Accent/warning color (orange)
var(--app-theme--error, #d32f2f)        // Error color (red)
var(--app-theme--error-dark, #ba1a1a)   // Dark error color
var(--app-theme--error-bg, #ffebee)     // Error background (light red)
var(--app-theme--surface, #fafafa)      // Card/surface background (light gray)
var(--app-theme--border, #e0e0e0)       // Border color (gray)
```
