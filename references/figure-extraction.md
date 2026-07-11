# Figure and table extraction

Open this reference when extracting and placing figures from a PDF.

## Rendering pages

Use PyMuPDF (fitz) to render each page at 200 DPI as JPEG:

```python
import fitz
from PIL import Image

doc = fitz.open(paper_path)
for i, page in enumerate(doc):
    pix = page.get_pixmap(dpi=200)
    img = Image.frombytes("RGB", [pix.width, pix.height], pix.samples)
    img.save(f"page{i+1}.jpg", quality=92)
```

## Locating figures

1. Read the extracted text to find figure captions (e.g., "Fig. 1", "Figure 2").
2. Identify which page each figure appears on.
3. The figure image area typically lies above its caption on the page.

## Tight cropping

When cropping a figure:
- Crop only the figure/table content area, not the whole page
- Use the smallest rectangle that contains the full visual object
- Exclude page headers, footers, surrounding prose, and unrelated margins
- Exclude the figure caption text (keep it separate)
- If the crop box is uncertain, mark it as approximate rather than enlarging it
- Save cropped figures as JPEG (quality 92) to `assets/`

For multi-part figures (Fig 1a-d, Fig 1e-h), crop each part separately if they form distinct visual groups.

```python
# Example: crop a figure region from a rendered page
page_img = Image.open("page2.jpg")
# Estimate crop region from figure position on page
# (adjust coordinates based on visual inspection of where figures sit)
fig = page_img.crop((left, top, right, bottom))
fig.save("assets/Fig1.jpg", quality=92)
```

## Placement in the reading notes

- Place each figure at its first substantive mention in the body text — not at the end
- If the PDF layout places the figure before the body text discusses it, still place it near the relevant discussion
- If a later section references the same figure, link back to it instead of duplicating
- Keep figure, caption, and reading note together as a single block

## Figure block shape

In the HTML output, each figure block should contain:

1. Figure number + title (bold)
2. The cropped image
3. Original English caption
4. Chinese caption translation
5. Reading note (阅读提示): 1-2 sentences pointing out what to inspect

```html
<figure>
  <figcaption>
    <strong>Fig. 1 | [Short translated title]</strong>
  </figcaption>
  <img src="assets/Fig1.jpg" alt="Fig. 1">
  <figcaption>
    <strong>Original caption:</strong> [original English caption text]<br>
    <strong>中文图注:</strong> [faithful Chinese translation]<br>
    <strong>阅读提示:</strong> [what to inspect and why it matters]
  </figcaption>
</figure>
```

## Precision

Precision matters more than convenience. A slightly smaller but correct crop is better than a wider crop that includes unrelated page content.
