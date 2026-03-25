# Design System Reference

Use this reference only for UI Mode of `system-design-interview-simulator`.

## Purpose

Provide a clean, interview-focused visual system for a single-file HTML simulator. Keep the look
professional and practical: high contrast, intentional spacing, and no generic purple-gradient AI style.

## Design Tokens

```css
:root {
  --color-bg: #f7f6f3;
  --color-bg-alt: #efede8;
  --color-surface: #ffffff;
  --color-surface-alt: #f9f8f5;
  --color-text: #22201d;
  --color-text-muted: #6a645d;
  --color-border: #ddd8cf;
  --color-accent: #0f766e;
  --color-accent-hover: #0d665f;
  --color-accent-soft: #ddf2ef;
  --color-success: #1f8a4c;
  --color-warning: #b56718;
  --color-danger: #b03434;

  --font-display: "Space Grotesk", "Avenir Next", "Segoe UI", sans-serif;
  --font-body: "Source Sans 3", "Segoe UI", sans-serif;
  --font-mono: "JetBrains Mono", "Menlo", monospace;

  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.35rem;
  --text-2xl: 1.8rem;

  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-10: 2.5rem;

  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 18px;

  --shadow-sm: 0 1px 2px rgba(34, 32, 29, 0.06);
  --shadow-md: 0 8px 24px rgba(34, 32, 29, 0.1);

  --duration-fast: 150ms;
  --duration-normal: 280ms;
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
}
```

## Layout Guidance

- Use a two-column layout on desktop: left for interview controls and transcript, right for notes/score preview.
- Collapse to one column on mobile (`max-width: 860px`).
- Keep content width readable (`max-width: 1200px`) with generous vertical spacing.
- Use card surfaces to separate: setup, active question, controls, transcript, and debrief.

## Typography Guidance

- Headings: `--font-display`, semibold/700.
- Body: `--font-body`, normal/400-500.
- Technical snippets and command labels: `--font-mono`.
- Keep paragraphs concise; prefer bullets and labeled sections for interview flow clarity.

## Color and Status Usage

- `--color-accent`: active phase, selected difficulty, primary buttons.
- `--color-success`: positive feedback in debrief.
- `--color-warning`: partial coverage or cautionary notes.
- `--color-danger`: missed core areas.
- Avoid heavy gradients; use subtle background alternation and borders for structure.

## Motion Guidance

- Add only meaningful transitions: phase change, new transcript message, scorecard reveal.
- Use short fades and slight vertical motion (`transform: translateY(6px)`).
- Avoid decorative animations that distract from interview content.

## Accessibility and Responsiveness

- Ensure contrast ratio is readable for text and controls.
- Make all controls keyboard reachable.
- Keep tap targets at least 40px high.
- Support small screens by stacking panels and keeping sticky action controls near the bottom.
