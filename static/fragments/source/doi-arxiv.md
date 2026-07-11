# Source: DOI / arXiv identifier

The user provides a bare DOI or arXiv ID.

1. Resolve the identifier:
   - For DOI: Use WebFetch on `https://doi.org/{DOI}` to find the paper page.
   - For arXiv: Use WebFetch on `https://arxiv.org/abs/{ID}`.
2. Determine the available format (PDF, HTML, or both).
3. Re-route to the appropriate source fragment (pdf-text, scanned-pdf, or html).
4. If the paper is behind a paywall and no preprint is available, note this and ask the user if they have access.
