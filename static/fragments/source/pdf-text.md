# Source: selectable-text PDF

The PDF has an extractable text layer.

- Use `pdftotext -layout` to extract the text layer; do not OCR.
- Process the entire document, not just the first pages.
- Watch for multi-column layouts: recover natural reading order from pdftotext output (which preserves layout order).
- Keep ligatures, hyphenated line breaks, superscripts, subscripts, and math symbols intact.
- Rejoin words split across line breaks.
- Figures and tables are images embedded in the page — crop them using PyMuPDF page rendering per `references/figure-extraction.md`.
- If some pages lack a text layer, treat those pages with the `scanned-pdf` fragment rules and mark confidence notes.
