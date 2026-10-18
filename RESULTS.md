# Results

## Notebook-output metrics

### Structured Q-CHAT-10-derived classification

The notebook has 1,054 rows, split into 843 training and 211 test samples.

| Model | Hold-out accuracy | Macro precision | Macro recall | Macro F1 | 5-fold CV accuracy |
|---|---:|---:|---:|---:|---:|
| Random Forest | 0.9621 | 0.9555 | 0.9555 | 0.9555 | 0.9597 ± 0.0165 |
| K-Nearest Neighbours | 0.9431 | 0.9259 | 0.9461 | 0.9349 | 0.9300 ± 0.0300 |
| XGBoost | 0.9858 | 0.9779 | 0.9897 | 0.9835 | 0.9763 ± 0.0135 |
| Logistic Regression | 0.9526 | 0.9413 | 0.9487 | 0.9449 | 0.9573 ± 0.0261 |

The XGBoost notebook reports AUC-ROC of 0.9997. Cross-validation is run on the training split, whereas the main comparison metrics above are from the 211-sample hold-out test set.

### Free-text classification

The BERT notebook cleans 333 rows to 332, then splits 232/50/50 into train/validation/test.

| Metric | Output |
|---|---:|
| Test accuracy | 0.8800 |
| 95% Wilson interval for accuracy | [0.7619, 0.9438] |
| Macro precision | 0.8917 |
| Macro recall | 0.8766 |
| Macro F1 | 0.8782 |
| AUC-ROC | 0.9792 |
| 5-fold CV accuracy (mean ± std) | 0.8825 ± 0.0423 |
| Test sample count | 50 |



