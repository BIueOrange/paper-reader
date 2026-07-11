---
name: paper-reader
description: Read academic papers (PDF, DOI, arXiv, or pasted text) and produce structured reading notes with extracted figures, source-grounded annotations, and a critical analysis section. Trigger when the user mentions 读论文、文献阅读、论文笔记、分析文章、帮我读这篇、paper notes、literature review, or provides a paper file/URL with intent to understand or analyze it. Produces a browser-viewable HTML reading note with figures embedded in-situ. Unlike nature-reader (full bilingual translation), this skill produces critical reading notes — extracting key information plus analysis, not translating every paragraph.
version: 2.0.0
---

# Paper Reader — Router

Split into a thin router (this file) and a static layer loaded on demand. Do not apply logic from memory; load fragments as directed.

## Routing protocol

### 1. Load manifest and core

Read [manifest.yaml](manifest.yaml). Then read every file listed under `always_load`.

### 2. Detect source format

Decide `source_format` using the manifest's `detect` hints. State the detected value in one short line before processing.

### 3. Load the matching source fragment

Read only the file mapped for the detected `source_format`. Do not read every fragment.

### 4. Build the reading notes

Apply loaded material in priority order:
1. Core principles (`static/core/principles.md`)
2. Source-format fragment — how to extract text, figures, tables
3. Reading workflow (`static/core/workflow.md`)
4. Figure extraction rules (`references/figure-extraction.md`)
5. Output contract (`static/core/output-contract.md`)
6. Critical analysis framework (`references/critical-analysis.md`)

### 5. Use references on demand

- Detailed figure cropping → `references/figure-extraction.md`
- HTML output template → `references/output-spec.md`
- Critical analysis dimensions → `references/critical-analysis.md`
