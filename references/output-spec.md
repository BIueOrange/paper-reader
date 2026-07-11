# HTML output specification

The primary output is a single self-contained HTML file with embedded CSS. Use this template as the starting structure and adapt section lengths proportionally to paper complexity.

## Design principles

- Clean, minimal, editorial — inspired by Nature Communications layout
- Generous whitespace, single column (max-width ~760px), centered
- Serif body text (Times New Roman / 宋体), monospace for DOI
- Figures are full-width within the content column, bordered and captioned
- Color palette: restrained. One accent color (#2468b0). Cards for analysis use muted border-left colors.
- No external dependencies — all CSS inline

## Required sections (in order)

1. **Header**: paper title, author list, affiliation, journal/year, DOI
2. **One-liner**: standout callout box (accent color left border)
3. **研究动机** (Motivation)
4. **核心方法** (Core Method)
5. **实验结果** (Experiments & Results) — figures and tables embedded near the relevant discussion
6. **结论** (Conclusions)
7. **批判性分析** (Critical Analysis) — 5-dimension card grid
8. **与我何干** (Personal Relevance)
9. **值得深挖的引用** (References to Follow Up)
10. **Footer**: generation date, source paper

## Figure blocks within the flow

Figures and tables are part of the narrative, not an appendix. Place them at their first substantive mention, whether that is the method or results section. Each figure block:

```html
<figure>
  <figcaption><strong>Fig. N | [Chinese short title]</strong></figcaption>
  <img src="assets/FigN.jpg" alt="Fig. N">
  <figcaption>
    <strong>Original caption:</strong> [English caption]<br>
    <strong>中文图注:</strong> [Chinese translation]<br>
    <strong>阅读提示:</strong> [1-2 sentences]
  </figcaption>
</figure>
```

Give every substantive HTML block a stable `id` and a visible source pointer. For example:

```html
<section id="S012" data-source="p.3 S012">
  <p class="source-anchor">来源: p.3 S012</p>
  <p>论文证据: ...</p>
</section>
```

Use `论文证据` for statements grounded in the paper. Put interpretations in a visually distinct `分析推断` block and list the source IDs that support it. Figure and table blocks use `F001`/`T001` IDs and name both their caption ID and placement block.

For paired figures placed side-by-side, use a CSS grid:

```html
<div class="figure-row">
  <figure>...</figure>
  <figure>...</figure>
</div>
```

## Critical analysis cards

Use a 2-column grid of cards, each with a colored left border:
- green (#2e7d32): positive (Novelty)
- red (#c62828): negative (Limitations)
- amber (#f57f17): neutral (Reproducibility, Gap to Practice, Open Questions)

## Responsive notes

- Side-by-side figures and analysis cards stack to single column on narrow screens (< 640px)
- Images use `max-width: 100%` to avoid overflow
- Font size scales from 17px body to 14px for captions and metadata

## Math rendering

Default: plain text (no LaTeX). Use Unicode and plain notation:
- Subscripts: H₂O → H2O, x_i → x_i
- Greek: α → alpha, β → beta
- Fractions: a/b
- Sums: sum_{i=1}^{n}

Only use LaTeX ($$...$$) when the user explicitly requests it.

## Supporting evidence files

Keep `source_map.json` alongside the HTML. It must include paper metadata plus an entry for every `S`, `C`, `F`, and `T` ID used in the page. Each entry records the source page or section, type, confidence, and references to connected figures/tables. `reading_notes.md` records draft status, unavailable sections, OCR uncertainty, approximate crops, and the exact source version used.
