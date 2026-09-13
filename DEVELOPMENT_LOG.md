# Development Log — Good Practices for AI-Assisted Coding

This document records the key decisions and iterations made during the development of the manual (`Good_Practices_AI_Coding.tex`) and the companion Quarto Beamer presentation (`AI_assisted_coding.qmd`).

---

## Origin and context

The material was developed during a conversation between Giorgio Arcara and Claude (Anthropic) about how to maintain genuine coding comprehension in the LLM era. The core discussion identified three target audiences and their distinct risks:

- **Experienced programmers** — risk of atrophying problem-decomposition skills by outsourcing cognitive work to LLMs
- **Junior researchers** — risk of mistaking operational familiarity for understanding; building fluency without a mental model
- **Research context specifically** — the mental model is the product, not just the code output; velocity at the cost of comprehension is a net loss

---

## Key conceptual decisions

### "The mental model is the product"
The central argument: in research, code is a means, not a deliverable. The real output is a claim about the world, and that claim is only as solid as the researcher's understanding of the pipeline that produced it. This was explicitly distinguished from industry contexts where working code *is* the deliverable.

### The predict → observe → update loop
Used as a framing device to explain *why* LLMs are problematic for learning: they short-circuit the loop by handing you the answer before you wrestle with the problem, bypassing the Update step that builds mental models.

**Important caveat (confirmed in conversation):** this is not a named established framework. It is a synthesis of well-grounded ideas from:
- Constructivist learning theory (Piaget, Vygotsky)
- Deliberate practice (Ericsson)
- Productive failure (Kapur)
- Bayesian reasoning and scientific method

It should not be cited as if it were a specific named theory. If citations are needed, the above sources are the honest reference points.

### "Define the problem first"
Added later in the session after Giorgio noted that in research, the aim of coding is to solve a problem — and that defining the problem is therefore a prerequisite step. This was incorporated as:
- A dedicated section in the LaTeX manual (Section 3, before the audience-specific practices)
- A dedicated slide in the presentation ("Before any practice: define the problem")
- A header row in the Quick Reference table

The key point: an LLM is good at solving the problem you give it — the risk is giving it the wrong problem because you have not thought it through yourself first.

---

## Structure of the manual

| Section | Content |
|---|---|
| Introduction | LLMs as powerful but risky; "the mental model is the product" |
| The Core Problem | Predict → observe → update loop; how LLMs bypass it; risks by audience |
| Define the Problem First | Universal prerequisite: define input, output, and success criteria before coding or prompting |
| Practices for Experienced Programmers | Trace before accepting; design first; code without LLM; seek friction |
| Practices for Junior Researchers | Blank-page reconstruction; inverted rubber duck; tests before code; bug journal; one variable at a time; decompose before prompting |
| Quick Reference | Side-by-side table with universal principle as header |

---

## Files and locations

| File | Location |
|---|---|
| LaTeX manual | `ONDALab-AI-guide/Good_Practices_AI_Coding.tex` |
| Quarto presentation | `Presentations/2025-05-AI-assited-coding/AI_assisted_coding.qmd` |
| Humorous opening figure | `Figures/AGC_chisafare.jpg` ("Chi sa fare, sa capire") |
| ONDA logo | `Figures/ONDA_logo_v12.png` |

---

## Iterations and fixes

- **Encoding fix**: original template used `\usepackage[latin1]{inputenc}`; changed to `[utf8]` to support Italian characters (è, etc.)
- **Opening figure**: `AGC_chisafare.jpg` (a meme reading *"Chi sa fare, sa capire — Non è un proverbio, Giacomo. È la vita."*) added as humorous opening page in the manual and first slide in the presentation
- **"Mental model" section expansion**: originally one paragraph; expanded to a dedicated subsection with an explicit list of consequences of lacking a mental model
- **AI disclaimer**: added to the title page of the LaTeX manual — notes the document was drafted in collaboration with Claude, with the author retaining intellectual ownership
- **Presentation text fitting**: all dense slides had `\small` added, `\vspace` reduced from `0.5em` to `0.3em`, and `\footnotesize` used in the Summary columns to prevent overflow with the Metropolis Beamer theme

---

## Quarto presentation notes

- Format: Beamer (PDF), Metropolis theme, no custom `.sty` files
- Rendered with `xelatex` via Quarto
- Figures needed in `Figures/` subfolder alongside the `.qmd`: `LogoSanCamilloIRCCS_Unipd_alpha.png`, `CC_license_3_0.png`, `AGC_chisafare.jpg`
- To render: `quarto render AI_assisted_coding.qmd` from the presentation folder
