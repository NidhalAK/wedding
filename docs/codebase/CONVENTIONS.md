# Coding Conventions

## Core Sections (Required)

### 1) Naming Rules

| Item | Rule | Example | Evidence |
|------|------|---------|----------|
| Files/assets | lowercase, underscore/hyphen separated | `anime_source_couple.png`, `video-intro-marriage.mp4` | scan.txt "DIRECTORY TREE" |
| Section IDs | `sec-<name>` | `sec-hero`, `sec-program` | [index.html#L503](../../index.html#L503) |
| CSS classes | BEM-style `block__element--modifier` | `.story-video__unmute`, `.dove--left` | [index.html#L249](../../index.html#L249) |
| JS functions/vars | lowerCamelCase, `var` declarations | `setLang`, `scrollToSection`, `updateScroll` | [index.html#L800](../../index.html#L800) |
| CSS tokens | `--kebab-case` custom properties | `--gold-deep`, `--font-ar-body` | [index.html#L16](../../index.html#L16) |

### 2) Formatting and Linting

- Formatter: none configured — scan.txt "LINTING AND FORMATTING CONFIG"
- Linter: none configured
- Enforced rules: none automated; style is manual/consistent (2-space indentation, single file)
- Run commands: none

### 3) Import and Module Conventions

- No module system; single file with inline `<style>` and `<script>`.
- External resources loaded via `<link>` (Google Fonts) and inline `<svg>`; no JS imports.
- Behavior isolated in IIFEs to avoid global leakage — [index.html#L847](../../index.html#L847).

### 4) Error and Logging Conventions

- No structured error handling or logging.
- User-facing fallbacks use `alert()` (RSVP, music placeholders) — [index.html#L935](../../index.html#L935).
- `music.play().catch(function(){})` silently swallows autoplay rejection — [index.html#L871](../../index.html#L871).

### 5) Testing Conventions

- No tests present. [TODO] no test file naming/location rule exists.

### 6) Evidence

- [index.html](../../index.html)
- docs/codebase/.codebase-scan.txt

## Extended Sections (Optional)

### Repo-specific branching conventions

Observed git branches suggest a versioned-iteration naming scheme (`premiere-version`, `first-version`, `Second-version`, `main`) — scan.txt "GIT RECENT COMMITS". Note the inconsistency: `Second-version` is capitalized while others are lowercase. [ASK USER] confirm intended branch naming scheme.
