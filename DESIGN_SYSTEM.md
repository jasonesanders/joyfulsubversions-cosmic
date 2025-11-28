# Design System Documentation

This document explains the design system for Joyful Subversions. All styles are defined in `/src/styles/global.css`.

## Philosophy

**Single Source of Truth**: All design tokens (colors, fonts, spacing) are defined once in `global.css`. Update them there to change the entire site.

**Semantic Classes**: Instead of repeating long utility strings, use pre-built component classes that describe *what* the element is, not *how* it looks.

## Color Palette

```css
--color-void-black: #050505      /* Background */
--color-off-white: #F0F0F0       /* Primary text */
--color-mint-cream: #D4F5D1      /* Accent */
--color-electric-blue: #0000AA   /* Highlight */
```

**Usage in HTML:**
```html
<div class="bg-void-black text-off-white">
```

## Typography

### Font Families

- **Spectral**: Used for headings (serif, elegant)
- **JetBrains Mono**: Used for body text (monospace, technical)

### Component Classes

#### `.hero-heading`
Large display text for hero sections
```html
<h1 class="hero-heading">Joyful Subversions</h1>
```

#### `.section-heading`
Major section titles
```html
<h2 class="section-heading">Your guide to the future.</h2>
```

#### `.subsection-heading`
Smaller section titles
```html
<h3 class="subsection-heading">About Us</h3>
```

#### `.body-text`
Standard paragraph text
```html
<p class="body-text">This is body copy.</p>
```

#### `.body-text-lg`
Larger, emphasized paragraphs
```html
<p class="body-text-lg">Important information.</p>
```

## Spacing

We follow a **4-point spacing system**. All margins, paddings, and gaps should be multiples of 4px (0.25rem).

### Common Values
- **4px** (`0.25rem`): `p-1`, `m-1`, `gap-1`
- **8px** (`0.5rem`): `p-2`, `m-2`, `gap-2`
- **16px** (`1rem`): `p-4`, `m-4`, `gap-4`
- **24px** (`1.5rem`): `p-6`, `m-6`, `gap-6`
- **32px** (`2rem`): `p-8`, `m-8`, `gap-8`
- **48px** (`3rem`): `p-12`, `m-12`, `gap-12`
- **64px** (`4rem`): `p-16`, `m-16`, `gap-16`

### Guidelines
- Avoid arbitrary values like `13px` or `21px`.
- Use consistent spacing for related elements (e.g., all section headings have `mb-8` or `mb-12`).
- Use `gap` utilities for grid and flex layouts instead of margins on children when possible.

## Layout Components

#### `.section-container`
Standard full-height section, centered content
```html
<section class="section-container">
  <!-- Content -->
</section>
```

#### `.section-container-left`
Full-height section, left-aligned content
```html
<section class="section-container-left">
  <!-- Content -->
</section>
```

#### `.section-container-top`
Full-height section, top-aligned content (for scrolling content)
```html
<section class="section-container-top">
  <!-- Content -->
</section>
```

#### `.content-wrapper`
Constrains content to readable width (max-width: 4xl)
```html
<div class="content-wrapper">
  <!-- Content -->
</div>
```

## Interactive Components

#### `.link-hover`
Standard link with underline on hover
```html
<a href="/" class="link-hover">Link</a>
```

#### `.card-hover`
Subtle hover effect for cards
```html
<div class="card-hover">Card content</div>
```

#### `.glass-card`
Glass morphism card style
```html
<div class="glass-card">
  <!-- Card content -->
</div>
```

## Best Practices

### ✅ DO

```html
<!-- Use semantic component classes -->
<h1 class="hero-heading">Title</h1>

<!-- Combine with utility classes when needed -->
<h1 class="hero-heading text-center">Centered Title</h1>
```

### ❌ DON'T

```html
<!-- Don't repeat long utility strings -->
<h1 class="font-spectral text-7xl md:text-9xl font-normal tracking-tight">Title</h1>
```

## Updating Styles

### To change a heading size globally:
Edit the `.hero-heading` class in `global.css`:
```css
.hero-heading {
    @apply font-spectral text-8xl md:text-10xl font-normal tracking-tight;
}
```

### To add a new color:
1. Add it to `@theme` in `global.css`:
```css
--color-sunset-orange: #FF6B35;
```

2. Use it with Tailwind utilities:
```html
<div class="bg-sunset-orange">
```

### To add a new component class:
Add it to `@layer components` in `global.css`:
```css
.special-button {
    @apply px-6 py-3 bg-electric-blue text-off-white rounded-lg hover:opacity-80;
}
```

## Questions?

- **"Can I still use regular Tailwind utilities?"** Yes! Component classes work alongside utilities.
- **"What if I need a one-off style?"** Use utilities directly. Component classes are for *repeated* patterns.
- **"How do I know what classes are available?"** Check `global.css` under `@layer components`.
