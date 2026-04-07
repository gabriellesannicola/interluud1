# interluud — Design System

> The complete design language for interluud.com. Reference this when building or editing any page.

---

## Brand Personality

**"Measured clarity"** — the intersection of a high-end architecture firm and a wellness brand. Warm but exact. Calming but not soft. Like a brilliant therapist who also ran a successful company.

- NOT: Headspace-style pastel blobs
- NOT: Corporate blue and clean grid
- NOT: Glassmorphism, cyan/purple gradients, neon, generic AI aesthetics
- YES: Editorial calm meets intelligent precision

---

## Typography

```css
/* Import */
@import url('https://fonts.googleapis.com/css2?family=Cormorant:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap');

--font-display: 'Cormorant', Georgia, serif;   /* All headlines, quotes, numbers */
--font-body:    'DM Sans', system-ui, sans-serif; /* All body text, UI, labels */
```

### Scale & usage
| Role | Font | Size | Weight | Notes |
|------|------|------|--------|-------|
| Hero headline | Cormorant | clamp(3.8rem, 6.2vw, 7.5rem) | 300 | letter-spacing: -0.025em |
| Section headline | Cormorant | clamp(2rem, 3.2vw, 3.6rem) | 300 | letter-spacing: -0.015em |
| Card headline | Cormorant | clamp(1.3rem, 1.7vw, 1.65rem) | 400 | — |
| Quote / testimonial | Cormorant italic | clamp(1.2rem, 1.7vw, 1.55rem) | 400 italic | — |
| Display numbers | Cormorant | clamp(2rem, 2.8vw, 2.8rem) | 300 | letter-spacing: -0.02em |
| Body copy | DM Sans | clamp(0.9rem, 1.05vw, 1rem) | 300 | line-height: 1.65 |
| Labels / eyebrows | DM Sans | 0.73–0.78rem | 500 | letter-spacing: 0.12–0.14em, uppercase |
| Nav links | DM Sans | 0.78rem | 400 | letter-spacing: 0.08em, uppercase |

### Key rules
- Italic Cormorant is used for emotional emphasis (not strong/bold)
- `<strong>` in Cormorant = weight 500 (not bold)
- Sienna colour on italic text = signature accent moment
- Never mix weights closer than 300/500 — the contrast is the point

---

## Colour Palette

```css
:root {
  --cream:       oklch(96.5% 0.012 85);   /* Page background */
  --parchment:   oklch(93%   0.018 82);   /* Section backgrounds, cards */
  --ink:         oklch(20%   0.025 65);   /* Primary text, dark sections */
  --ink-soft:    oklch(42%   0.022 65);   /* Secondary text, captions */
  --sienna:      oklch(52%   0.15  42);   /* Brand accent — ALL interactive elements */
  --sienna-pale: oklch(88%   0.05  42);   /* Light sienna tint for backgrounds */
  --white:       oklch(99%   0.005 85);   /* Card backgrounds, nav on scroll */
}
```

### Colour rules
- **Sienna is the only accent** — used for: eyebrow labels, italic emphasis, borders on testimonials, hover states, CTA buttons, step numbers, footer mark
- **Never use pure #000 or pure #fff** — always the warm-tinted versions above
- **Dark sections** (process): `background: var(--ink)`, text in `oklch(92% 0.012 85)`, muted text in `oklch(55% 0.02 65)`
- **Border colour on light backgrounds**: `oklch(88% 0.016 82)`
- **Border colour on dark backgrounds**: `oklch(32% 0.02 65)`

---

## Spacing

```css
--pad: clamp(1.5rem, 5.5vw, 6.5rem);   /* Consistent horizontal page padding */
```

### Vertical rhythm
- Between sections: `clamp(6rem, 12vw, 14rem)` — generous, editorial
- Within sections: `4–5rem` for related groups
- Between items: `1–2.5rem` depending on relationship

### Grid patterns
- **Two-column hero**: `55fr 45fr` with 4rem gap
- **Three-column services**: `repeat(3, 1fr)` with vertical dividers (no gap, padding instead)
- **Four-column process**: `repeat(4, 1fr)` same approach
- **Statement**: `1fr 2.4fr` — label left, content right

---

## Components

### Primary button
```css
.btn {
  font: 500 0.8rem/1 'DM Sans';
  letter-spacing: 0.09em;
  text-transform: uppercase;
  padding: 1rem 2rem;
  border: 1px solid var(--ink);
  background: var(--ink);
  color: var(--white);
  transition: background 0.22s, border-color 0.22s;
}
.btn:hover { background: var(--sienna); border-color: var(--sienna); }
```

### Nav
- Fixed, `backdrop-filter: blur(14px)`, 92% opacity cream background
- Logo: Cormorant 1.45rem weight 400
- Links: DM Sans 0.78rem uppercase, fade on hover
- CTA pill: ink background → sienna on hover

### Testimonial / quote card
- White background, `border-left: 3px solid var(--sienna)`
- Cormorant italic for quote text
- DM Sans 0.76rem uppercase sienna for attribution

### Section eyebrow
```css
.eyebrow {
  display: flex; align-items: center; gap: 0.75rem;
  font: 500 0.75rem 'DM Sans';
  letter-spacing: 0.13em; text-transform: uppercase;
  color: var(--sienna);
}
.eyebrow::before { content:''; width:2rem; height:1px; background:var(--sienna); }
```

### Dividers
- Use whitespace — no visible `<hr>` elements
- When a structural line is needed: `1px solid oklch(88% 0.016 82)` on light, `1px solid oklch(32% 0.02 65)` on dark

---

## Motion

```css
/* Scroll reveal */
.reveal {
  opacity: 0;
  transform: translateY(22px);
  transition: opacity 0.72s cubic-bezier(0.16, 1, 0.3, 1),
              transform 0.72s cubic-bezier(0.16, 1, 0.3, 1);
}
.reveal.in { opacity: 1; transform: none; }

/* Stagger delays */
.d1 { transition-delay: 0.1s; }
.d2 { transition-delay: 0.2s; }
.d3 { transition-delay: 0.3s; }
.d4 { transition-delay: 0.4s; }
```

- Easing: `cubic-bezier(0.16, 1, 0.3, 1)` — ease-out-expo. Never bounce or elastic.
- Hero elements reveal on load with 80ms + i×130ms stagger
- All other elements reveal on scroll via IntersectionObserver (threshold: 0.12)
- Hover transitions: 0.22s ease — buttons, links
- Marquee band: 28s linear infinite, `-50%` translateX

---

## Marquee band
- `background: var(--ink)`
- Cormorant italic 0.95rem, colour `oklch(85% 0.012 85)`
- Sienna 4px dot separators
- Items: divorce coaching · breakup recovery · separation decisions · co-parenting strategy · identity rebuilding · confidence restoration · platonic breakups · practical action plans

---

## What NOT to do
- No glassmorphism
- No cyan/purple/blue gradients
- No neon accents
- No gradient text
- No rounded rectangles with a coloured left border (different from the testimonial card — that uses full white bg)
- No system fonts
- No stock photography in the hero
- No centered layouts (always left-aligned)
- No equal visual weights — everything needs clear hierarchy
