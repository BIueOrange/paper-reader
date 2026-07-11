# Core principles

Produce structured critical reading notes, not a full bilingual translation. This skill is for understanding and analyzing papers, not for creating a paragraph-level bilingual reader (use nature-reader for that).

## Non-negotiable defaults

Do not degrade the output to:
- A Chinese-only summary without figures
- A few bullet points detached from source locations
- Only the abstract or introduction
- A paper review without figure evidence

If the PDF is too long or partially unreadable, still create a draft and mark missing content. Do not silently skip sections.

## What the output IS

- A single HTML file with professional typography and figures embedded inline
- Figures cropped tightly and placed near their first substantive mention — not at the end
- Original figure captions preserved with Chinese translations
- Critical analysis alongside extracted content (not instead of it), visibly marked as analysis
- Stable source anchors (`p.3 S012`, `p.4 C001`, `F001`, `T001`) for every substantive paper claim
- Key English technical terms preserved alongside Chinese

## What the output is NOT

- A paragraph-level full paper translation
- A machine translation dump
- Figures dumped at the bottom of the file
- A chat-friendly summary without visual evidence
- Critical analysis presented as though it were a paper claim

## Evidence discipline

Build the notes from a stable evidence map before writing narrative prose. Every paper-backed statement must carry a page plus block ID where available. When pages are unavailable, use a section plus block ID and state that limitation.

Keep two kinds of statements distinct:
- **论文证据**: a finding, method detail, number, or author-stated limitation with source anchors
- **分析推断**: the skill's interpretation, critique, or extrapolation, with the evidence IDs it relies on

Never fabricate an anchor, a figure crop, a metric, or a missing section. Record retrieval, OCR, layout, and crop uncertainty in `reading_notes.md`.

## Figure philosophy

Figures are not decoration — they are evidence. Every figure in the notes should:
- Be cropped tightly (only the figure content, no headers/footers/margins)
- Appear where the text first discusses it, not at the end of the file
- Carry its original caption and a Chinese caption translation
- Include a brief "阅读提示" (reading note) pointing out what to inspect

## Quality bar

Good output feels like a well-designed journal club presentation:
- A colleague can understand the paper's contribution, method, and limitations without reading the original
- Every figure is inspectable in context
- Critical analysis is specific, not generic praise
- The reader can trace paper claims to a page and stable block, then tell them apart from analysis
