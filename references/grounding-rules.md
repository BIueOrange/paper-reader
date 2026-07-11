# Grounding rules

## Evidence and inference

Use `论文证据` only for information present in the source. Cite the page plus stable block ID, and include a caption or table ID when visual evidence matters.

Use `分析推断` for the skill's critique, comparison, or extrapolation. Name the evidence IDs that motivate the inference and avoid wording that implies the authors made the claim.

If a requested detail is absent, say `论文未明确说明`. Do not infer a number, method detail, dataset property, or limitation from the title or abstract alone.

## Follow-up questions

1. Search `source_map.json` for the relevant blocks.
2. Answer from the mapped source first.
3. Cite page and ID, such as `p.5 S021` or `p.6 C003`.
4. Include the connected figure/table when it is part of the evidence.
5. State any extraction or source-version limitation from `reading_notes.md`.

## Minimum source map shape

```json
{
  "paper": {"title": "", "source_type": "pdf|html|doi|arxiv|text", "source_path": "", "version_read": ""},
  "blocks": [{"id": "S001", "page_or_section": "p.1", "type": "paragraph|caption|table", "confidence": "high|medium|low", "refs": ["F001"]}],
  "figures": [{"id": "F001", "caption_id": "C001", "asset_path": "assets/Fig1.jpg", "placed_after": "S012", "crop_confidence": "high|medium|low"}]
}
```
