# Source: scanned / image-only PDF

The PDF pages render as images with no extractable text layer.

- Render pages at a readable resolution and use an available OCR or vision-capable extraction tool. Do not rely on a provider-specific tool name.
- Process all pages. Record any unreadable page or low-confidence block in `reading_notes.md` and `source_map.json`.
- Preserve uncertain wording instead of silently correcting it. Be especially cautious with numbers, units, symbols, gene/protein names, and chemical formulas.
- Figures: the entire page is an image, so crop figure regions from page renders using PyMuPDF. Estimate crop regions from layout (figure captions in the rendered text will guide positioning).
- Mark extraction confidence per block as high, medium, or low. Flag uncertain readings in the HTML rather than presenting them as settled text.
