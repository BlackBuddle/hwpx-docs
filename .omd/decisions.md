# Intro page (site/index.html): design decisions

Date: 2026-11-15. Surface: one static page for first-time visitors. Copy comes from README.md 0.3.0.

## Concepts

The oh-my-design CLI (`omd`) did not start on this Windows host (Node ESM path error), so the concept step was done by hand with the same rule: two candidates, identical real content, different structure.

| ID | Relationship | Desktop 1280 | Mobile 390 |
|---|---|---|---|
| A | Paper first: headline and install block on the left, a stack of three real Hangul-rendered pages on the right; capabilities in a two-column grid; 3x2 gallery | 3453 px tall | 4784 px tall |
| B | Page as an official document: centered title with double rule, meta table, numbered sections (가. 나. 다.), examples in a horizontal strip, "끝." at the end | 2712 px tall | 3275 px tall |

Captures are kept outside the repo, in the session work folder (`intro/captures/cand-a-*.png`, `cand-b-*.png`).

## Choice

A. A visitor sees real Hangul pages in the first screen, and the six examples stay visible in a grid. In B the examples come late and hide in a scroll strip, and the serif title depends on a Windows font.
No user was present to choose (child session); the choice is the session's and is reported to the orchestrator.

## Implementation notes

- Tokens: paper `#f6f4ee`, ink `#1c2230`, muted `#555d6c`, rule `#d9d6cc`, one accent `#a3301c` (kicker, link hover, focus ring). System fonts only, no web fonts, no scripts.
- Mobile: one column below 760 px; grid children get `min-width:0` so the install block scrolls inside itself (candidate A overflowed by 9 px).
- Added from the README: command names under each capability, a four-step "이렇게 씁니다" list that links to the README usage section.
- Slop check: no gradients, glows, emoji, gradient text or uppercase tracked labels; `unslop` was not needed.

# Icon and README head: design decisions

Date: 2026-11-15. Surfaces: `assets/icon.svg` (README head, 120 px), `site/icon.svg` (favicon and header mark, a copy so that `site/` stays self-contained). The README head follows a common centered layout (icon, name, one-line summary, link row, language row, badge row); no picture or wording was copied.

## Concepts

The omd CLI still does not start on Windows, so the concept step was done by hand: three flat, single-colour candidates on the same grey tile `#e4e1d8`, shapes only (no font). The Hangul letter ㅎ is built from a short bar, a long bar and a ring.

| ID | Structure | 16 px result |
|---|---|---|
| A | Solid ink page with a folded corner, ㅎ cut out of it | Page reads; the bars of ㅎ blur |
| B | Ink outline page, ㅎ drawn in ink inside | Weakest: outline and letter merge |
| C | Accent page (`#a3301c`) that fills most of the tile, folded corner, large ㅎ cut out | Page, fold and ㅎ all read |

Candidate SVGs and the comparison page are outside the repo, in the session work folder (`intro/icon/concept-a.svg`, `concept-b.svg`, `concept-c.svg`, `compare.html`; capture `intro/captures/icon-concepts.png`). To switch, copy another candidate over `assets/icon.svg` and `site/icon.svg`.

## Choice

C. It is the only candidate whose letter is legible at 16 px, and the accent colour ties it to the intro page. The light tile keeps it visible on GitHub light (`#ffffff`) and dark (`#0d1117`) themes. No user was present to choose (child session); the choice is reported to the orchestrator.

## Revision 2: no jamo (same day)

User feedback on C: it looks too much like Hangul. A coloured rounded tile with one jamo is the shape of the Hancom Office app icons (Hangul, Hancell, Hanshow), and the README says the project has no relation to Hancom. New constraints: no Hangul letters or jamo, no single glyph on a coloured tile, no Hancom family colour (blue, green, orange) as the main colour, `#a3301c` as an accent only, shapes only, legible at 16 px on both GitHub themes.

All three new candidates use the neutral tile `#e4e1d8`, a white page with an ink (`#1c2230`) outline and folded corner, and the accent on one small part.

| ID | Symbol | Colour | 16 px result |
|---|---|---|---|
| D | Page with a table: an accent header row and four ink cells (forms, tables) | ink, accent header row | Page, header row and cells all read |
| E | Page with three text lines and a check badge (make and check) | ink, accent badge | Badge and lines merge; generic "verified file" icon |
| F | Page with XML angle brackets and an accent rule (OWPML is XML) | ink, accent rule | Brackets blur into a dot; reads as a generic code file |

Choice: D. It is the only new candidate whose symbol reads at 16 px, a table is what HWPX forms and reports are made of, the main colour is neutral ink on white, and the accent covers one row only. It does not use a glyph, so it does not look like a Hancom app icon. Candidates A, B, C (revision 1) and D, E, F stay in `intro/icon/`; capture `intro/captures/icon-concepts-v2.png`.

## README head notes

- Link row: intro page (`https://blackbuddle.github.io/hwpx-docs/`, one line in the source so that it can be deleted alone if Pages is not used), `#설치`, `#사용-예-프로젝트-계획-문서-만들기`, `docs/`.
- Language row: `한국어 · English` (`#english`).
- Badges, all shields.io `flat`, colour `a3301c`: license AGPL-3.0, version 0.3.0 (same as `.claude-plugin/plugin.json`), GitHub stars, Python 3.10+, Claude Code plugin. No download or social badges (no source for them).
