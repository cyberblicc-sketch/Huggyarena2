# Huggyarena2

This repository includes `HuggyArena.pdf` plus extracted outputs in multiple formats so the full document is easy to access, search, and verify.

## Repository content

- `HuggyArena.pdf` — original source document.
- `docs/HuggyArena.extracted.txt` — plain text, page-by-page extraction (best for grep/search tools).
- `docs/HuggyArena.extracted.md` — markdown extraction with per-page sections (best for human browsing).
- `docs/HuggyArena.extracted.json` — structured extraction (`total_pages` + `pages[]`) for programmatic use.
- `docs/HuggyArena.extraction-report.json` — verification metadata (page counts + SHA-256 hashes).

## Verification summary

- Total pages extracted: **80**
- Non-empty extracted pages: **80**
- Page boundaries are preserved in the TXT extraction with `===== PAGE N =====` markers.

## Notes

- Use TXT for quick text search, MD for readable sectioned viewing, and JSON for scripts/integrations.
- Some PDF parsing artifacts may remain where text wraps across page boundaries.
