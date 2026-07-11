# Output contract

## Required deliverables

Create a directory `{PaperShortTitle}_阅读笔记/` next to the source PDF. When the source path is unavailable, use the current workspace's output directory rather than assuming a Desktop path.

```
{PaperShortTitle}_阅读笔记/
├── {PaperShortTitle}_阅读笔记.html   # Primary output — browser-viewable
├── source_map.json                    # Stable evidence IDs and source locations
├── reading_notes.md                   # Retrieval, extraction, and uncertainty notes
└── assets/                          # Cropped figures
    ├── Fig1.jpg
    ├── Fig2.jpg
    └── ...
```

The HTML file is the primary artifact. `source_map.json` and `reading_notes.md` are supporting artifacts, not replacements for the note. Do NOT produce a plain Markdown file as the primary output unless the user explicitly asks for one.

If the source is incomplete, OCR is uncertain, or figures cannot be extracted, label the HTML as draft mode and explain the gap in `reading_notes.md`.

## Pre-response verification

Before declaring done, verify:
- [ ] HTML file exists and is valid (well-formed, all tags closed)
- [ ] Every `<img>` tag's `src` points to an existing file in `assets/`
- [ ] `source_map.json` parses and every HTML source anchor resolves to a mapped ID
- [ ] `reading_notes.md` records retrieval, OCR, layout, and crop uncertainty where applicable
- [ ] Metadata header includes title, authors, year, venue, and DOI when available; absent fields are marked unavailable
- [ ] One-sentence summary present
- [ ] All five content sections present (motivation, method, experiments, conclusions, key figures)
- [ ] Every figure block has: image + original caption + Chinese caption + reading note
- [ ] Critical analysis covers: novelty, limitations, reproducibility, gap to practice, open questions
- [ ] Personal relevance section present
- [ ] Formulas in correct format (plain text unless user requested LaTeX)
- [ ] The full paper was processed — not just the abstract
- [ ] Paper evidence and analytical inferences are visibly distinguished

## Tooling

- PDF text extraction: `pdftotext -layout` for selectable-text PDFs
- Figure extraction: PyMuPDF (fitz) for page rendering + cropping
- HTML rendering: open the HTML file in browser to verify before reporting done
