# Critical analysis framework

Every paper reading must include a critical analysis covering these five dimensions. Be specific — generic praise ("该方法很新颖") is not analysis.

## 1. 创新点 (Novelty)

What is genuinely new? Distinguish from incremental improvement.
- Is this a new problem formulation, a new method, a new dataset, or a new insight?
- What does this paper enable that was impossible before?
- Compare to the closest prior work — what's the delta?

Rule: If you can't name the specific delta, you haven't identified the novelty.

## 2. 局限性 (Limitations)

Every paper has limitations. Find them:
- Methodology weaknesses (assumptions, simplifications, experimental design)
- Scope limitations (single dataset, single material system, specific conditions)
- Missing comparisons, ablations, or baselines
- Statistical significance concerns (error bars, sample sizes)
- Overclaimed conclusions not fully supported by evidence

## 3. 可复现性 (Reproducibility)

Assess whether the work can be replicated:
- Code available? If claimed but no URL, flag it.
- Data available? Public dataset, on request, or not mentioned?
- Experimental details sufficient? Could a skilled practitioner reproduce from the Methods section?
- Hyperparameters, random seeds, environmental details provided?

## 4. 与实际应用的差距 (Gap to Practice)

How far is this from real-world deployment?
- Lab demonstration vs. production-ready?
- What engineering work would be needed to bridge the gap?
- Are there scale, cost, or reliability barriers?

## 5. 未回答的问题 (Open Questions)

What does this paper leave unanswered?
- Questions the authors explicitly flag as future work
- Questions you notice that the authors didn't address
- Logical next steps for the research community

## Writing guidelines

- Use bullet points, not paragraphs
- Be specific: "Only tested on Al9.5CrCoNi — unknown if CMRO exists in other H/MEA compositions" not "limited scope"
- Balance is key: a paper can be excellent AND have real limitations
- If a paper is genuinely weak in an area, say so directly — don't soften the critique
- Prefix paper-backed statements with `论文证据:` and cite page/block IDs.
- Prefix the skill's own interpretation with `分析推断:` and name the evidence IDs it relies on.
- Do not present an absence of reporting as evidence of absence; say `论文未明确说明` when the source is silent.
