---
name: paper-reader
description: Read academic papers (PDF, DOI, arXiv, or pasted text) and produce structured reading notes with extracted figures, source-grounded annotations, and a critical analysis section. Trigger when the user mentions 读论文、文献阅读、论文笔记、分析文章、帮我读这篇、paper notes、literature review, or provides a paper file/URL with intent to understand or analyze it. Produces a browser-viewable HTML reading note with figures embedded in-situ. Unlike nature-reader (full bilingual translation), this skill produces critical reading notes — extracting key information plus analysis, not translating every paragraph.
version: 2.1.0
---

# Paper Reader — Router

Split into a thin router (this file) and a static layer loaded on demand. Do not apply logic from memory; load fragments as directed.

## Routing protocol

### 1. Load manifest and core

Read [manifest.yaml](manifest.yaml). Then read every file listed under `always_load`.

### 2. Detect source format

Decide `source_format` using the manifest's `detect` hints. State the detected value in one short line before processing. A DOI or arXiv identifier is a resolution stage, not the final extraction stage: after resolving it, load the fragment for the retrieved PDF or HTML too.

### 3. Load the matching source fragment

Read only the selected fragment or fragments. Do not read every fragment. For a resolved DOI/arXiv source, load `doi-arxiv` first and then the fragment for the resolved artifact.

### 4. Build the evidence map before writing

Create stable IDs before drafting the notes:

- `S001`, `S002`, ... for substantive text blocks
- `C001`, `C002`, ... for captions
- `F001`, `F002`, ... for figures
- `T001`, `T002`, ... for tables

For every block, record its page or section, source type, extraction confidence, and links to related figures/tables. Store this in `source_map.json`. Keep paper evidence separate from the skill's critical-analysis inferences.

### 5. Build the reading notes

Apply material in this order:
1. Core principles (`static/core/principles.md`)
2. Source-format fragment — how to extract text, figures, tables
3. Reading workflow (`static/core/workflow.md`)
4. Figure extraction rules (`references/figure-extraction.md`) before cropping a figure or table
5. Output contract (`static/core/output-contract.md`) before creating the artifact
6. Critical analysis framework (`references/critical-analysis.md`) before writing the five analysis dimensions

### 6. Use references on demand

- Detailed figure cropping → `references/figure-extraction.md`
- HTML output template → `references/output-spec.md`
- Critical analysis dimensions → `references/critical-analysis.md`
- Follow-up answers and evidence/inference labels → `references/grounding-rules.md`

### 7. Answer follow-up questions from the artifact

When the user asks about a completed reading note, answer from `source_map.json` and the HTML anchors. Cite the exact page and block IDs, include the figure/table when it is part of the evidence, and say that the paper does not establish a point when the source is silent.
