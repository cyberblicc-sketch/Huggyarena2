# Huggyarena2

This repository includes `HuggyArena.pdf` plus extracted outputs in multiple formats so the full document is easy to access, search, and verify.

## Repository content

- `HuggyArena.pdf` — original source document.
- `docs/HuggyArena.extracted.txt` — plain text, page-by-page extraction.
- `docs/HuggyArena.extracted.md` — markdown extraction with per-page sections.
- `docs/HuggyArena.extracted.json` — structured extraction (`total_pages` + `pages[]`).
- `docs/HuggyArena.extraction-report.json` — verification metadata (page counts + SHA-256 hashes).

## Verification summary

- Total pages extracted: **80**
- Non-empty extracted pages: **80**
- Page boundaries are preserved in the TXT extraction with `===== PAGE N =====` markers.

## Notes

- Different output formats are provided intentionally so the PDF content can be consumed in different ways.
- Some PDF parsing artifacts may remain where text wraps across page boundaries.
