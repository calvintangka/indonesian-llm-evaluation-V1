# Indonesian–English LLM Evaluation: Code-Switching Stress Test

**Author:** Calvin Tangka

**Study period:** 3–7 May 2026

**Report correction:** 16 November 2026

**Contact:** fxcalvintangka@gmail.com

## Overview

This independent, single-annotator study explores how six language models handled ten Indonesian–English code-switching prompts. I scored 60 responses using a five-dimension weighted rubric and tracked three failure categories. It is a small exploratory evaluation, not a production benchmark or a definitive ranking of model capabilities.

The original 2026 report contained internal inconsistencies. This revision recalculates the tables below directly from the dimension scores in the published scoring workbook, corrects the CS-06 example arithmetic, removes unsupported conclusions and broken links, and discloses missing source records. The original report remains available in the repository's Git history. The workbook and original figures have not been modified.

## Design and scoring

Each of ten prompt IDs was evaluated for each of six models. The study tested language-direction instructions, bilingual register, terminology and cultural interpretation. The rubric uses a 1–5 score on each dimension:

| Dimension | Weight |
| --- | ---: |
| Accuracy | 20% |
| Instruction following | 30% |
| Bilingual language quality | 30% |
| Helpfulness and completeness | 15% |
| Format and presentation | 5% |

Composite = 0.20 × D1 + 0.30 × D2 + 0.30 × D3 + 0.15 × D4 + 0.05 × D5. Three separately logged flags cover language collapse, register inconsistency and surface compliance. Flags are not independent observations and a response can receive multiple flags.

## Results from the recorded scores

The following averages were independently recomputed from the 60 dimension-score rows in the [scoring workbook](Indonesian_LLM_Evaluation_Scoring_Sheet.xlsx), with three decimal places shown to avoid rounding ambiguity. Counts are numbers of flagged responses out of ten per model.

| Model label in workbook | Average composite | Language collapse | Register inconsistency | Surface compliance |
| --- | ---: | ---: | ---: | ---: |
| GPT 5.5 | 4.990 | 0 | 0 | 0 |
| Claude Opus 4.7 | 4.955 | 0 | 0 | 0 |
| Gemini Flash 3 | 4.020 | 0 | 1 | 0 |
| Meta Muse Spark | 3.045 | 2 | 6 | 4 |
| DeepSeek V3 | 3.055 | 1 | 5 | 5 |
| Qwen 3.6 | 3.380 | 0 | 5 | 2 |

These are results for this prompt set and annotator. They should not be interpreted as statistical significance, generalized model reliability, evidence of underlying architecture, or a recommendation for high-stakes deployment.

## Example: language-direction compliance

Prompt CS-06 asked the model to argue in Indonesian in response to an English argument. A fluent but English-led response could therefore miss a key instruction. The workbook records scores of 2, 2, 2, 3, 3 for Meta Muse Spark: applying the stated weights yields **2.20**, not 2.27 as in the original report. GPT 5.5's recorded 5, 5, 5, 5, 4 yields **4.95**, not 4.97. These are calculations from recorded scores, not independent verification of the original responses.

## Limitations and reproducibility

- One bilingual annotator scored ten prompts; no inter-annotator agreement was measured. The earlier report described repeat scoring, but paired original and repeat records have not been verified, so no drift-reliability conclusion is made here.
- The complete original prompt set and all 60 full responses are not present in this repository. The scoring workbook contains prompt summaries, dimension scores, flags and notes; this allows numerical checking but not independent re-scoring of the original responses. Do not treat the summaries as full prompts.
- The workbook lists GPT 5.5 via Outlier AI Playground, Claude Opus 4.7 via Claude Pro, Gemini Flash 3 via Google AI Studio, and the remaining three models via their listed provider interfaces. The original report also described Gemini as accessed via Google Gemini and gave conflicting general descriptions of platform access. The exact Gemini interface remains unresolved pending original records. Different interfaces and default settings are a potential confound.
- Model labels, versions and access details are reproduced from the records and have not been independently verified against provider logs. Results reflect the recorded May 2026 study, not current versions.
- The small, deliberately selected prompt set and urban Indonesian–English register limit generalization. There is no basis here for confidence intervals, claims of statistical significance, or broad product-selection conclusions.
- The workbook contains formulas without saved cached values in the inspected file. The numbers in this report were calculated from the five recorded scores per row using the weights above; spreadsheet viewers may need to recalculate formulas to show their own calculated cells.
- The original figures are retained as historical artifacts and were not regenerated or validated in this revision. If any figure conflicts with the recomputed table or the underlying scoring rows, use the scoring rows and stated formula; audit the figure before reuse.

## Files

- [Scoring workbook](Indonesian_LLM_Evaluation_Scoring_Sheet.xlsx): score rows, rubric, summary and failure-mode guide.
- `fig1_composite_scores.png` through `fig6_tier_summary.png`: historical figures; see the qualification above.
- [Report history](https://github.com/calvintangka/indonesian-llm-evaluation-V1/commits/main/README_evaluation_report.md): prior versions and corrections.

Future improvements include locating the original prompts and responses, resolving interface provenance, adding independent annotators and expanding the test set. This independent portfolio project is not sponsored by the model providers.

