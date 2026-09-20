# Architecture

## Core Sections (Required)

### 1) Architectural Style

- Primary style: Single-page, single-file static website (no framework, no backend)
- Why this classification: one `index.html` contains all markup, CSS, and JS; no manifest, build, or server — scan.txt "STACK DETECTION", [index.html](../../index.html)
- Primary constraints: everything runs client-side in the browser; progressive enhancement (feature-checks for `IntersectionObserver`); bilingual (FR default / AR RTL) toggled via `data-lang` on `<body>`

### 2) System Flow

```text
Browser loads index.html
  -> Intro overlay (pigeons + heart animation) plays, auto-closes after 5.6s or on skip
  -> startReveals() wires IntersectionObserver for .reveal elements
  -> User scrolls: scroll-progress bar + section-dot nav update on scroll
  -> Sections render: hero -> story(video) -> invite -> program(countdown, maps) -> rsvp
  -> Interactions: language switch, video unmute, lightbox, RSVP alert, music toggle
```

### 3) Layer/Module Responsibilities

| Layer or module | Owns | Must not own | Evidence |
|-----------------|------|--------------|----------|
| CSS `:root` tokens | Color palette + font variables | Behavior | [index.html#L16](../../index.html#L16) |
| Markup sections | Content + structure for each section | Logic/state | [index.html#L503](../../index.html#L503) |
| Inline `<script>` IIFEs | Feature behaviors (intro, video, petals, music) scoped to avoid globals | Styling | [index.html#L847](../../index.html#L847) |
| `setLang()` | Language + direction switching | Layout definition | [index.html#L800](../../index.html#L800) |

### 4) Reused Patterns

| Pattern | Where found | Why it exists |
|---------|-------------|---------------|
| IIFE module isolation | video, paris starfield, music, petals blocks | Avoid polluting global scope | 
| Feature detection / graceful degradation | `startReveals()` falls back if no `IntersectionObserver` | Support older browsers — [index.html#L879](../../index.html#L879) |
| Data-attribute-driven behavior | `data-target`, `data-set-lang`, `data-cd`, `data-full` | Decouple markup from JS lookups — [index.html#L447](../../index.html#L447) |
| CSS custom properties as design tokens | `:root` variables | Central theming — [index.html#L16](../../index.html#L16) |

### 5) Known Architectural Risks

- Monolithic single file (~971 lines) mixing structure, style, and behavior — hard to maintain/reuse; high churn on `index.html` (5 recent commits — scan.txt "HIGH-CHURN FILES").
- Placeholder integrations (RSVP, music) are non-functional stubs shipping `alert()` prompts — [index.html#L932](../../index.html#L932).
- Hardcoded event date/time and venue links; no data layer.

### 6) Evidence

- [index.html](../../index.html)
- docs/codebase/.codebase-scan.txt
