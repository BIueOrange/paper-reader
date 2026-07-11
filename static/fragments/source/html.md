# Source: publisher / preprint HTML

The user provides a URL to the paper's HTML version.

- Retrieve the article with an available browser or HTTP fetch tool.
- Extract the article body while excluding site navigation, cookie banners, advertisements, and related-article rails.
- Preserve section order, inline math, citation markers, figures, captions, and clean HTML tables.
- Download figure images if accessible; otherwise note them as "Figure [N]: 参见原文" with a description from the caption.
- Process the full article if accessible; record paywalls, JavaScript-only content, and missing sections in `reading_notes.md`.
