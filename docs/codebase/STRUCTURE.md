# Codebase Structure

## Core Sections (Required)

### 1) Top-Level Map

| Path | Purpose | Evidence |
|------|---------|----------|
| `index.html` | Entire application: markup, inline CSS, inline JS | [index.html](../../index.html) |
| `anime_source_couple.png` | Hero + gallery couple illustration | [index.html#L505](../../index.html#L505) |
| `anime_source_paris.png` | Gallery "Paris / Tour Eiffel" illustration | [index.html#L572](../../index.html#L572) |
| `video-intro-marriage.mp4` | Story-section video | [index.html#L548](../../index.html#L548) |
| `images/` | Asset folder (currently only `.DS_Store` tracked in working tree) | scan.txt "DIRECTORY TREE" |
| `.gitignore` | Ignores `.DS_Store` files | [.gitignore](../../.gitignore) |
| `docs/codebase/` | Generated codebase documentation (this skill) | this folder |

### 2) Entry Points

- Main runtime entry: `index.html` (opened directly by the browser)
- Secondary entry points: none
- How entry is selected: single file; no router or server

### 3) Module Boundaries

The whole app is one file. Logical boundaries exist as comment-delimited blocks inside the inline `<script>`:

| Boundary | What belongs here | What must not be here |
|----------|-------------------|------------------------|
| `<style>` block (L15–L437) | All CSS, design tokens in `:root` | Behavior/logic |
| `<body>` markup (L440–L793) | Semantic sections `#sec-hero` … `#sec-rsvp`, intro, lightbox | Business data / secrets |
| `<script>` block (L795–L969) | Language switch, scroll, video, intro, countdown, lightbox, RSVP, music, petals | Styling |

### 4) Naming and Organization Rules

- File naming pattern: lowercase with underscores/hyphens (`anime_source_couple.png`, `video-intro-marriage.mp4`)
- Section IDs follow `sec-<name>` (`sec-hero`, `sec-story`, `sec-invite`, `sec-program`, `sec-rsvp`) — [index.html#L447](../../index.html#L447)
- CSS uses BEM-ish naming (`.story-video__player`, `.intro__names`, `.dove--left`) — [index.html#L248](../../index.html#L248)
- Language visibility via `.lang-fr` / `.lang-ar` / `.only-fr` / `.only-ar` classes toggled by `body[data-lang]` — [index.html#L64](../../index.html#L64)

### 5) Evidence

- [index.html](../../index.html)
- docs/codebase/.codebase-scan.txt
