# Source: scanned / image-only PDF

The PDF pages render as images with no extractable text layer.

- Use the Read tool to view pages directly. Claude's vision can read text from page images.
- If the Read tool returns "[Unsupported Image]", render pages as JPEG via PyMuPDF and read those.
- Process all pages. Mark any pages that could not be read in `翻译说明:` notes.
- Figures: the entire page is an image, so crop figure regions from page renders using PyMuPDF. Estimate crop regions from layout (figure captions in the rendered text will guide positioning).
- Mark extraction confidence as lower than pdf-text. Flag uncertain readings.
