# Source: selectable-text PDF

The PDF has an extractable text layer.

- Prefer `pdftotext -layout` or an equivalent selectable-text extractor; do not OCR readable text.
- Process the entire document, not just the first pages.
- Build source-map entries for every substantive text block, caption, figure, and table before writing the note.
- Watch for multi-column layouts: recover natural reading order rather than trusting raw extraction order.
- Keep ligatures, hyphenated line breaks, superscripts, subscripts, and math symbols intact.
- Rejoin words split across line breaks.
- Figures and tables are images embedded in the page — crop them using PyMuPDF page rendering per `references/figure-extraction.md`.
- If some pages lack a text layer, apply the `scanned-pdf` rules to those pages and record per-block confidence in `reading_notes.md` and `source_map.json`.
