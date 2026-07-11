# Reading workflow

Six steps for every paper-reading job.

## 1. Assess the paper

Identify paper type and structure before extracting:
- Discovery / mechanism paper → focus on evidence chain and figures
- Methods / algorithm paper → focus on technical approach and comparisons
- Review / perspective → focus on framework and key references

Quickly skim to understand: what section structure, how many figures, what's the core claim.

## 2. Build the evidence map

Map the entire document before drafting. Use stable IDs:
- `S001`, `S002`, ... for body text
- `C001`, `C002`, ... for captions
- `F001`, `F002`, ... for figures
- `T001`, `T002`, ... for tables

For each entry, record page or section, content type, reading order, extraction confidence, related figure/table IDs, and where a figure/table is first substantively discussed. Save the map as `source_map.json`. If the source is incomplete, keep the available IDs and record the gap rather than inventing missing content.

## 3. Extract all substantive content

Process the entire document. Do not stop at abstract or introduction.

Extract into these categories:
- **Metadata**: title, authors, affiliations, year, venue, DOI
- **One-liner**: the paper's core contribution in one Chinese sentence
- **Motivation**: what problem, why important, what gap
- **Method**: technical approach, key innovations, core formulas (plain text by default)
- **Experiments & Results**: setup, datasets, baselines, metrics, key quantitative findings
- **Conclusions**: main takeaways
- **Figures & Tables**: every figure/table with caption

Assign stable source anchors using page plus block IDs (for example `p.2 S014`, `p.3 C002`). For pasted text with no pages, use the nearest section plus the block ID.

## 4. Extract and crop figures

Crop each figure/table into `assets/` using the rules in `references/figure-extraction.md`. Render pages at 200 DPI via PyMuPDF, then crop tight bounding boxes around each figure/table. Connect each asset to its `F`/`T` ID, caption ID, source page, and placement block in the evidence map.

## 5. Write the critical analysis

Apply the framework in `references/critical-analysis.md`. Be specific — "方法新颖" is not analysis. Explain WHY and HOW. Label every item as `论文证据` or `分析推断`; analytical items must cite the evidence IDs that motivate them.

## 6. Write the personal relevance section

Connect to the user's stated interests and current goal. Do not assume a field; when no context is available, explain the paper's likely use cases and state that personal relevance is provisional.

## 7. Generate the HTML output

Use the template in `references/output-spec.md`. Verify:
- Every figure reference in the HTML has a corresponding file in `assets/`
- Every figure has original caption + Chinese translation + reading note
- Critical analysis covers all five dimensions
- Source anchors (page numbers) are present on key claims
- `source_map.json` parses and its IDs match the HTML anchors
- `reading_notes.md` discloses missing content, low-confidence extraction, or approximate crops
