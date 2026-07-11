# Output contract

## Required deliverables

Create a directory `{PaperShortTitle}_阅读笔记/` next to the source PDF (or on Desktop if source path unknown).

```
{PaperShortTitle}_阅读笔记/
├── {PaperShortTitle}_阅读笔记.html   # Primary output — browser-viewable
└── assets/                          # Cropped figures
    ├── Fig1.jpg
    ├── Fig2.jpg
    └── ...
```

The HTML file is the primary artifact. Do NOT produce a plain Markdown file as the primary output unless the user explicitly asks for one.

## Pre-response verification

Before declaring done, verify:
- [ ] HTML file exists and is valid (well-formed, all tags closed)
- [ ] Every `<img>` tag's `src` points to an existing file in `assets/`
- [ ] Metadata header complete (title, authors, year, venue, DOI)
- [ ] One-sentence summary present
- [ ] All five content sections present (motivation, method, experiments, conclusions, key figures)
- [ ] Every figure block has: image + original caption + Chinese caption + reading note
- [ ] Critical analysis covers: novelty, limitations, reproducibility, gap to practice, open questions
- [ ] Personal relevance section present
- [ ] Formulas in correct format (plain text unless user requested LaTeX)
- [ ] The full paper was processed — not just the abstract

## Tooling

- PDF text extraction: `pdftotext -layout` for selectable-text PDFs
- Figure extraction: PyMuPDF (fitz) for page rendering + cropping
- HTML rendering: open the HTML file in browser to verify before reporting done
