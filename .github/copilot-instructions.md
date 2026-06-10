# Copilot Instructions for Massively Portfolio Template

## Project Overview
This is a **Massively** HTML5 UP template - a responsive, article-oriented website template built for portfolio use. The template features a full-screen background image with parallax scrolling, scroll effects, and a mobile-first responsive design.

## Architecture & Key Components

### HTML Structure Pattern
- **Three-page structure**: `index.html` (main), `generic.html` (article template), `elements.html` (component showcase)
- **Consistent layout wrapper**: All pages use `#wrapper` → `#header` → `#nav` → `#main` → `#footer` structure
- **Navigation state management**: Use `.active` class on nav links to indicate current page
- **Scroll-triggered animations**: Elements use `scrolly` class for smooth scroll behavior

### SASS Architecture (assets/sass/)
```
libs/           # Core variables and mixins
├── _vars.scss  # Color palette, typography, sizing tokens
├── _mixins.scss # Reusable style mixins
└── _breakpoints.scss # Responsive breakpoint definitions

base/           # Foundation styles
components/     # Reusable UI components (buttons, forms, icons)
layout/         # Page structure components (header, nav, footer)
```

### Responsive Breakpoint System
Uses a 7-tier breakpoint system defined in both SASS and JavaScript:
- `xxsmall`: ≤360px, `xsmall`: 361-480px, `small`: 481-736px
- `medium`: 737-980px, `large`: 981-1280px, `xlarge`: 1281-1680px, `default`: ≥1681px

### Color System
Theme uses a palette-based color system in `_vars.scss`:
- **Primary palette**: white bg (\#ffffff), dark text (\#212931), accent blue (\#18bfef)
- **Alt palette**: light gray variant for sections
- **Invert palette**: dark theme for hero sections
- Access colors via `_palette()` function: `_palette(accent)`, `_palette(alt, bg)`

## Development Patterns

### Styling Components
- **Use existing component patterns**: Check `components/` before creating new styles
- **Color variants**: Apply `@include color($palette)` mixin for theme variants
- **Icons**: Use Font Awesome classes with semantic `<span class="label">` for accessibility

### JavaScript Enhancements
- **Parallax backgrounds**: Use `$().parallax()` method for background image effects
- **Scroll effects**: Leverage Scrollex library for scroll-triggered animations
- **Navigation**: Mobile nav panel auto-toggles based on breakpoints

### Adding New Content
- **Articles/Posts**: Follow `<section class="post">` structure from `generic.html`
- **Gallery items**: Use `<article>` with `.image.main` wrapper for featured images
- **Form elements**: Reference `elements.html` for proper markup patterns

## File Relationships
- **SASS compilation**: `main.scss` imports all partials → compiles to `main.css`
- **JavaScript dependencies**: jQuery → utility libs → `main.js` (load order matters)
- **Images**: Background images referenced in `_wrapper.scss` expect `images/bg.jpg` and `images/overlay.png`

## Customization Guidelines
- **Color changes**: Modify palette in `_vars.scss`, use existing color function calls
- **Typography**: Font stacks defined in `$font` map, use heading vs body family appropriately
- **Layout modifications**: Wrapper width, padding, margins controlled via `$size` map
- **New breakpoints**: Update both SASS `@include breakpoints()` and JS `breakpoints()` calls

## Common Tasks
- **Adding portfolio items**: Clone article structure from `index.html` main section
- **Theme customization**: Start with `_vars.scss` palette and size adjustments
- **Mobile optimization**: Test across all 7 breakpoints, mobile-first approach
- **Performance**: Minimize changes to compiled `main.css`, work in SASS partials