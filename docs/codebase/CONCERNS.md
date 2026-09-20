# Codebase Concerns

## Core Sections (Required)

### 1) Top Risks (Prioritized)

| Severity | Concern | Evidence | Impact | Suggested action |
|----------|---------|----------|--------|------------------|
| high | RSVP (resolved) | [index.html](../../index.html) | Now opens WhatsApp to `33658117207` with a pre-filled bilingual message | Wired on branch `review-after-skills` |
| med | Music toggle is a placeholder; `music.mp3` source is commented out | [index.html#L786](../../index.html#L786), [index.html#L945](../../index.html#L945) | Music button shows an alert instead of playing | Add `music.mp3` and uncomment `<source>` |
| med | Monolithic 971-line single file mixing HTML/CSS/JS | [index.html](../../index.html) | Hard to maintain; highest-churn file | Consider splitting CSS/JS if project grows |
| low | Referenced `images/web/*.jpg` (in git history) not present in working tree | scan.txt "HIGH-CHURN FILES" vs `find images` (only `.DS_Store`) | Potential broken references if used | Confirm which images are needed |

### 2) Technical Debt

| Debt item | Why it exists | Where | Risk if ignored | Suggested fix |
|-----------|---------------|-------|-----------------|---------------|
| Placeholder integrations | Built UI first, integrations deferred | RSVP L932, music L786 | Core features unusable | Provide real endpoints/assets |
| Hardcoded event data | No data layer for a one-off site | countdown target date L887, venue map links L666–L752 | Manual edits error-prone | Acceptable for single event; document values |
| No build/minification | Static hand-authored file | whole repo | Large inline assets (58KB HTML) served unminified | Optional: minify for production |

### 3) Security Concerns

| Risk | OWASP category | Evidence | Current mitigation | Gap |
|------|----------------|----------|--------------------|-----|
| External links open new tab | A01 (limited) | [index.html#L666](../../index.html#L666) | `rel="noopener"` present on map links | None significant |
| Third-party CDN (Google Fonts) | A08 (supply chain) | [index.html#L10](../../index.html#L10) | `preconnect` only | No SRI hash; low risk for fonts |
| No user input processing | A03 | N/A | Site is read-only; RSVP is a stub | If RSVP form added, validate/sanitize input |

### 4) Performance and Scaling Concerns

| Concern | Evidence | Current symptom | Scaling risk | Suggested improvement |
|---------|----------|-----------------|--------------|-----------------------|
| Large unoptimized assets | scan.txt largest files: PNGs ~2.1–2.4MB, MP4 ~2.4MB | Slow first load on mobile | Bandwidth cost | Compress images, use responsive/`webp`, poster for video |
| Video `preload` (resolved) | [index.html](../../index.html) | Was `preload="auto"`; now `preload="metadata"` | — | Fixed on branch `review-after-skills` |

### 5) Fragile/High-Churn Areas

| Area | Why fragile | Churn signal | Safe change strategy |
|------|-------------|--------------|----------------------|
| `index.html` | All logic + style in one file | 5 recent commits (scan.txt "HIGH-CHURN FILES") | Change one section block at a time; verify in browser |

### 6) `[ASK USER]` Questions

1. [ASK USER] ~~What should the RSVP button do~~ — resolved: opens WhatsApp chat to `33658117207` with a pre-filled confirmation message.
2. [ASK USER] Do you want background music? If so, provide `music.mp3` (and confirm autoplay expectations). ([index.html#L786](../../index.html#L786))
3. [ASK USER] Where will this be deployed (GitHub Pages, Netlify, other)? This affects asset paths and any build step.
4. [ASK USER] Are the `images/web/*.jpg` files from git history still needed, or fully replaced by the `anime_source_*.png` assets?
5. [ASK USER] Confirm the wedding date `2026-12-30T18:00:00+01:00` used by the countdown is correct. ([index.html#L887](../../index.html#L887))

### 7) Evidence

- docs/codebase/.codebase-scan.txt
- [index.html](../../index.html)
