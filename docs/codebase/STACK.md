# Technology Stack

## Core Sections (Required)

### 1) Runtime Summary

| Area | Value | Evidence |
|------|-------|----------|
| Primary language | HTML5 + CSS3 + vanilla JavaScript (ES5-style `var`) | [index.html](../../index.html) |
| Runtime + version | Web browser (no server runtime); `<!DOCTYPE html>` | [index.html#L1](../../index.html#L1) |
| Package manager | None — no manifest files found | scan.txt "STACK DETECTION" |
| Module/build system | None — single self-contained HTML file, no bundler | scan.txt "MONOREPO / ENTRY POINTS" |

### 2) Production Frameworks and Dependencies

No JavaScript frameworks or npm dependencies. Only external assets loaded at runtime.

| Dependency | Version | Role in system | Evidence |
|------------|---------|----------------|----------|
| Google Fonts (Cormorant Garamond, Great Vibes, Amiri, Aref Ruqaa, El Messiri) | latest (CDN) | Typography for FR/AR display + body text | [index.html#L10](../../index.html#L10) |
| Browser `IntersectionObserver` API | native | Scroll-reveal animations | [index.html#L879](../../index.html#L879) |

### 3) Development Toolchain

| Tool | Purpose | Evidence |
|------|---------|----------|
| None detected | No linter/formatter/build config in repo | scan.txt "LINTING AND FORMATTING CONFIG" |

### 4) Key Commands

```bash
# No install/build/test commands — static site.
# To preview locally, open the file directly or serve the folder:
python3 -m http.server 8000   # then open http://localhost:8000
```

### 5) Environment and Config

- Config sources: none (no `.env`, no config files) — scan.txt "ENVIRONMENT VARIABLE TEMPLATES"
- Required env vars: none
- Deployment/runtime constraints: needs the sibling asset files (`anime_source_couple.png`, `anime_source_paris.png`, `video-intro-marriage.mp4`) served alongside `index.html`; internet access required for Google Fonts and Google Maps links.

### 6) Evidence

- [index.html](../../index.html)
- [.gitignore](../../.gitignore)
- docs/codebase/.codebase-scan.txt
