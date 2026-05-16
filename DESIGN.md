# Design System — Hamza Anjum CV

## Color Strategy: Committed (dark drenched surface, accent carries identity)

Physical scene: a technical hiring manager opens this PDF at their desk at 10am, comparing 6 candidates. The CV needs to stop the scroll immediately. Dark background + high-contrast blue accent makes the name and section headers land before anything else.

## Colors (OKLCH)

```
--color-bg:         oklch(10% 0.008 264);   /* near-black, slightly blue-tinted */
--color-surface:    oklch(14% 0.009 264);   /* card surface, same hue family */
--color-border:     oklch(28% 0.010 264);   /* subtle dividers */
--color-text:       oklch(91% 0.008 254);   /* off-white, warm enough to read */
--color-muted:      oklch(60% 0.012 264);   /* dates, location, secondary labels */
--color-accent:     oklch(68% 0.18 254);    /* GitHub blue — headings, links, chips */
--color-accent-dim: oklch(18% 0.06 254);    /* chip/tag background */
--color-rule:       oklch(52% 0.16 145);    /* terminal green — the HR divider only */
--color-chip-border:oklch(48% 0.18 254);    /* skill chip border */
```

Hex fallbacks (for print / older browsers):
- bg: #0D1117, surface: #161B22, border: #30363D
- text: #E6EDF3, muted: #8B949E, accent: #58A6FF
- accent-dim: #1C2D40, rule: #238636, chip-border: #1F6FEB

## Typography

- **Font:** JetBrains Mono — weights 400 (body), 500 (labels/chips), 700 (name, job titles, section headers)
- **Scale:**
  - Name: 28px / 700
  - Job title: 13px / 700
  - Section header: 11px / 700 / uppercase / letter-spacing: 1.5px
  - Body / bullets: 11.5px / 400
  - Small / dates / muted: 10.5px / 400
- **Line height:** 1.7 (generous for monospace readability)
- **Body line length:** capped at ~70ch in the main column

## Layout

- Page: A4 — 794px wide at 96dpi, min-height 1123px
- Padding: 40px (screen) / 20mm 18mm (print)
- Two-column grid: `62% 1fr` with 32px gap
- Full-width header above the grid
- **Spacing rhythm:** section gap 24px, entry gap 16px — not uniform; entries breathe, sections breathe more

## Components

### Section header
- `//` prefix written in HTML text
- `11px / uppercase / 700 / letter-spacing: 1.5px / color: accent`
- `border-bottom: 1px solid border-color` + 12px margin-bottom
- Never gradient text. Never gradient anything.

### Experience entry
- Flex row: logo circle (24px) + title stack + dates (right-aligned via justify-content: space-between)
- Logo: border-radius 50%, 1px border in border-color, object-fit: contain, white bg for transparent PNGs
- Dates: muted color, white-space: nowrap
- Bullets: `›` via ::before pseudo (U+203A), accent color, no list-style
- Entry separator: 1px solid, very subtle (`oklch(18% 0.008 264)`)

### Skill chip
- `<code>` element
- `9.5px / 500 / monospace`
- `border: 1px solid chip-border / background: accent-dim / border-radius: 4px / padding: 3px 7px`
- Flex-wrap wrapping grid

### Cert badge
- Inline pill: `9px / 700 / color: accent / border: 1px solid accent / border-radius: 3px / padding: 1px 4px`
- No background fill — bordered only
- Beside the cert name in muted text

## Motion

None. CVs don't animate.

## Absolute bans

All shared bans from impeccable apply. Additionally:
- No border-left accent stripes on section headers
- No gradient text on the name
- No card containers around sections (flat layout only)
- No box-shadow on the page container in print
