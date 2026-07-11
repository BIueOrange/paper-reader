# Reading workflow

Six steps for every paper-reading job.

## 1. Assess the paper

Identify paper type and structure before extracting:
- Discovery / mechanism paper → focus on evidence chain and figures
- Methods / algorithm paper → focus on technical approach and comparisons
- Review / perspective → focus on framework and key references

Quickly skim to understand: what section structure, how many figures, what's the core claim.

## 2. Extract all substantive content

Process the entire document. Do not stop at abstract or introduction.

Extract into these categories:
- **Metadata**: title, authors, affiliations, year, venue, DOI
- **One-liner**: the paper's core contribution in one Chinese sentence
- **Motivation**: what problem, why important, what gap
- **Method**: technical approach, key innovations, core formulas (plain text by default)
- **Experiments & Results**: setup, datasets, baselines, metrics, key quantitative findings
- **Conclusions**: main takeaways
- **Figures & Tables**: every figure/table with caption

Assign stable source anchors: use page numbers as source identifiers (p.2, p.3-4).

## 3. Extract and crop figures

Crop each figure/table into `assets/` using the rules in `references/figure-extraction.md`. Render pages at 200 DPI via PyMuPDF, then crop tight bounding boxes around each figure.

## 4. Write the critical analysis

Apply the framework in `references/critical-analysis.md`. Be specific — "方法新颖" is not analysis. Explain WHY and HOW.

## 5. Write the personal relevance section

Connect to the user's known interests (materials science + ML by default). Be honest if the connection is weak.

## 6. Generate the HTML output

Use the template in `references/output-spec.md`. Verify:
- Every figure reference in the HTML has a corresponding file in `assets/`
- Every figure has original caption + Chinese translation + reading note
- Critical analysis covers all five dimensions
- Source anchors (page numbers) are present on key claims
