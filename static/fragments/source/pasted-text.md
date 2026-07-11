# Source: pasted text

The user pastes paper text directly.

- Treat the pasted text as the source of truth. Build sequential source IDs even when page numbers are unavailable, and use section anchors where possible.
- Use the text as-is. No figure extraction is possible without source images or a PDF.
- Note under each figure reference: "Figure [N]: 用户未提供PDF，图参见原文" with caption description from the text.
- Process all pasted content. If only a partial paper was pasted, label the note as draft mode and record which sections are missing.
- Preserve citation markers, equations, units, and symbols as pasted. Do not backfill omitted sections from memory.
- Still produce the full reading notes structure — don't skip critical analysis just because figures are missing.
