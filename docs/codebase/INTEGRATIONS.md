# External Integrations

## Core Sections (Required)

### 1) Integration Inventory

| System | Type (API/DB/Queue/etc) | Purpose | Auth model | Criticality | Evidence |
|--------|---------------------------|---------|------------|-------------|----------|
| Google Fonts | CDN / static asset | Web typography (FR + AR fonts) | None (public CDN) | med (visual) | [index.html#L10](../../index.html#L10) |
| Google Maps (search URL) | External deep link | Directions to 3 wedding venues | None | low | [index.html#L666](../../index.html#L666) |
| WhatsApp (RSVP) | External deep link (`wa.me`) | Guests confirm attendance via chat to `33658117207` | None | high | [index.html](../../index.html) |
| Background music (`music.mp3`) | Local audio asset | Ambient music | None | low | [index.html#L786](../../index.html#L786) |

### 2) Data Stores

| Store | Role | Access layer | Key risk | Evidence |
|-------|------|--------------|----------|----------|
| None | Static site has no data store | N/A | N/A | scan.txt "STACK DETECTION" |

### 3) Secrets and Credentials Handling

- Credential sources: none — no API keys, tokens, or `.env` files present (scan.txt "ENVIRONMENT VARIABLE TEMPLATES").
- Hardcoding checks: no secrets found in `index.html`.
- Rotation or lifecycle notes: N/A.

### 4) Reliability and Failure Behavior

- Retry/backoff: none.
- Timeout policy: none.
- Fallbacks: Google Maps links open in new tab with `rel="noopener"` — [index.html#L666](../../index.html#L666); music autoplay rejection caught silently — [index.html#L871](../../index.html#L871).

### 5) Observability for Integrations

- Logging around external calls: none.
- Metrics/tracing: none.
- Missing visibility gaps: no analytics; no error reporting.

### 6) Evidence

- [index.html](../../index.html)
- docs/codebase/.codebase-scan.txt
