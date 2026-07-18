# Conspiracies Paper

Repository for my research project "Conspiracy Beliefs as Intelligence Signaling: Modeling Social Context, Impression Motivation, and Individual Differences." Preregistered experiment (*N* = 500), manuscript in preparation. Preregistration is available online through [OSF](https://osf.io/9prnb/overview?view_only=ca6cbe91f6f440199ade76681c38301a).

Participants read an ambiguous fictional crisis scenario and wrote an interpretation of it under a 2 (motivation: intelligence vs. control) × 2 (audience: public vs. private) between-subjects design. Written responses were scored for conspiracism computationally; scenario-specific conspiracy belief was measured afterward.

`Conspiracies_Public.csv` is the final analysis dataset (500 rows, one per participant) and contains everything needed to reproduce the manuscript: demographics, the full written response, LIWC-22 output, and both text-based conspiracism scores.

`Conspiracies_2.docx` is the full Qualtrics survey export -- consent text, all individual-difference items, the crisis scenario, the four condition prompts verbatim, manipulation checks, and the adapted GCBS.

## To run

1. Collect responses in Qualtrics using `Conspiracies_2.docx` as the survey instrument, and export. Run the written responses through LIWC-22.
2. Score each response for conspiracism with ConspEmoLLM (1--5 rating) and compute LOCO discriminability as cosine similarity to the LOCO conspiracy centroid minus similarity to the mainstream centroid, using `all-MiniLM-L6-v2` embeddings. I did this in Python, but here have only included the R code for simplicity.
2. Either use your output or use `Conspiracies_Public.csv` directly, then run `Analysis_Conspiracies.qmd` in R for all analyses reported in the manuscript. Output tables and models are written to `outputs/`, with `_MANIFEST.csv` listing every file produced.

## Data

Multi-item scales are stored as **raw, unscored items** exactly as Qualtrics recorded them. Reverse coding and scale means are computed in `Analysis_Conspiracies.qmd`, so all scoring decisions are visible.

Prolific IDs and all other identifiers have been removed.

## Dependencies

R: tidyverse, broom, psych, ppcor, effectsize, emmeans, pwr, conflicted

LIWC-22 (Boyd et al., 2022) is proprietary; its output is included here, but regenerating it requires a license. LOCO (Miani et al., 2021) is available at [OSF](https://osf.io/snpcg/); ConspEmoLLM (Liu et al., 2024) at [GitHub](https://github.com/lzw108/ConspEmoLLM).
