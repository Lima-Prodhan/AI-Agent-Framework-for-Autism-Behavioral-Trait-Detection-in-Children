# Results and limitations

## Notebook-output metrics used in this repository

### Structured Q-CHAT-10-derived classification

The notebook has 1,054 rows, split into 843 training and 211 test samples. Results from the saved notebook output:

| Model | Hold-out accuracy | Macro precision | Macro recall | Macro F1 | 5-fold CV accuracy |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0.9621 | 0.9555 | 0.9555 | 0.9555 | 0.9597 ± 0.0165 |
| K-Nearest Neighbours | 0.9431 | 0.9259 | 0.9461 | 0.9349 | 0.9300 ± 0.0300 |
| XGBoost | 0.9858 | 0.9779 | 0.9897 | 0.9835 | 0.9763 ± 0.0135 |
| Logistic Regression | 0.9526 | 0.9413 | 0.9487 | 0.9449 | 0.9573 ± 0.0261 |

The XGBoost notebook reports AUC-ROC of 0.9997. Cross-validation is run on the training split, whereas the main comparison metrics above are from the 211-sample hold-out test set.

### Free-text classification

The BERT notebook cleans 333 rows to 332, then splits 232/50/50 into train/validation/test.

| Metric | Saved notebook output |
|---|---:|
| Test accuracy | 0.8800 |
| 95% Wilson interval for accuracy | [0.7619, 0.9438] |
| Macro precision | 0.8917 |
| Macro recall | 0.8766 |
| Macro F1 | 0.8782 |
| AUC-ROC | 0.9792 |
| 5-fold CV accuracy (mean ± std) | 0.8825 ± 0.0423 |
| Test sample count | 50 |

## Source inconsistencies that should remain visible

1. **BERT test accuracy conflict:** the BERT notebook’s saved final output reports 88.00% on 50 test samples; the report/poster generally use 88.0%. Presentation slide 23 reports 92.16% on 51 samples, and slide 21 uses batch size 8 while the report/notebook use batch size 16. These appear to represent a different run or stale reporting. This repository uses the saved notebook output as its primary result and does not combine the two.
2. **BERT AUC wording:** the notebook output and the report’s results table report AUC-ROC 0.9792, but some report/poster prose rounds or states the value as 0.96. Use the tabulated notebook value only with the dataset/split caveat.
3. **XGBoost CV wording:** the notebook output and report table give mean CV accuracy 0.9763 ± 0.0135 (approximately 97.63% ± 1.35 percentage points). A narrative paragraph in the report instead says approximately 98.58% ± 0.41%, which does not match the saved CV output.
4. **Report appendix:** the final appendix pages contain unrelated text about lung histopathology classification, CNN backbones, FastAPI, and lung cancer detection. This is inconsistent with the autism-screening capstone and should be corrected in the report before public portfolio publication. The report is included unchanged here to preserve the submitted source artifact.
5. **Agent LLM identifier:** the report's methods section mentions GPT-4o mini, while its limitations section names `gpt-oss-120b`. The actual app/API implementation is not included in the supplied ZIP, so the deployed model cannot be verified from source.
6. **Agent implementation not provided:** report and poster describe a LangGraph multi-agent flow and Streamlit app, but only two model-training notebooks are in the archive. Claims about implementation behavior and the “anti-hallucination” boundary cannot be code-audited from this repository's included source.

## Research and generalisation limitations

- The text dataset is small (332 rows; 50 held-out test samples), reflected in the broad 95% Wilson interval. Results may vary materially with another split or dataset.
- The text model is evaluated on a random split from the same source dataset, not an independent institution, cohort, language, or prospective study.
- Text augmentation can change meaning despite protected vocabulary and filtering; its clinical fidelity was not independently evaluated.
- The 14-trait extraction described in the report uses a constrained LLM call, and the report states there are no sentence-level ground-truth multi-label annotations for reliable trait-wise evaluation.
- The concern tiers are a project design, not a clinically validated severity scale.
- The structured model uses public data labels; high retrospective accuracy does not make the model a diagnostic instrument.
- No clinical validation, clinician-led safety evaluation, prospective study, or actual caregiver usability evaluation is included in the supplied materials.
- A clean, repeatable run from a fresh environment has not been performed for this repository package.
