# An AI Agent Framework for Autism Behavioral Trait Detection in Children

**Capstone project | Computer Science & Engineering | East West University | April 2026**

This repository packages the source materials supplied for the capstone project: two model-training notebooks, the submitted report, poster, presentation, application screenshots extracted from the report, and a source/results audit.

> **Important safety note:** This is an academic research prototype, not a diagnostic tool and not a substitute for assessment by a qualified healthcare professional. The dataset metrics below are retrospective results on public datasets, not evidence of clinical validation or suitability for real-world decisions about children.

## Project overview

The report describes a dual-input workflow for child behavioural-trait screening research:

1. **Structured questionnaire path:** an XGBoost model trained on Q-CHAT-10-derived binary features, compared with Random Forest, K-Nearest Neighbours (KNN), and Logistic Regression.
2. **Free-text path:** a fine-tuned `bert-base-uncased` classifier for ASD/Non-ASD labels on a small behavioural text dataset. The notebook uses synonym and contextual BERT masked-language-model augmentation on the training set.
3. **Agent experience described in the report:** a LangGraph workflow with supervisor, questionnaire, text, guidance, social-story, and visual-schedule agents; a fixed 14-trait taxonomy; and a Streamlit interface.

**Source-scope clarification:** the supplied ZIP contains only the two model-training notebooks—not the Python source for the described LangGraph/Streamlit application, the agent nodes, retrieval index/story library, or saved trained model files. Screenshots below are extracted from the report; they do not mean the app source code is included. See [`docs/AGENT_IMPLEMENTATION_SCOPE.md`](docs/AGENT_IMPLEMENTATION_SCOPE.md).

## Reported model results

The table uses the saved outputs in the supplied notebooks as the primary source for the reported metrics. These are not independently reproduced in a clean environment.

| Task | Model | Test accuracy | Macro precision | Macro recall | Macro F1 | AUC-ROC | Additional result |
|---|---|---:|---:|---:|---:|---:|---|
| Q-CHAT-10 structured | XGBoost | 98.58% | 0.9779 | 0.9897 | 0.9835 | 0.9997 | 5-fold CV accuracy: 0.9763 ± 0.0135 |
| Behavioural free text | Fine-tuned BERT | 88.00% | 0.8917 | 0.8766 | 0.8782 | 0.9792 | 95% Wilson CI for accuracy: [0.7619, 0.9438]; test n=50 |

The tabular notebook evaluates four models on an 80/20 stratified split of 1,054 records (843 train, 211 test). The text notebook cleans the supplied 333-row CSV to 332 records and uses a 70/15/15 stratified split (232 train, 50 validation, 50 test). Full metric details and source discrepancies are documented in [`docs/RESULTS_AND_LIMITATIONS.md`](docs/RESULTS_AND_LIMITATIONS.md).

## Screenshots from the submitted report

These are illustrative screenshots reproduced from the implementation chapter of the original capstone report. The repository does not include the application code needed to launch this interface.

![Application home screen](assets/app-screenshots/01-home-screen.png)

| Questionnaire result | Behavioural trait analysis |
|---|---|
| ![Questionnaire result](assets/app-screenshots/05-questionnaire-result.png) | ![Behavioural trait analysis](assets/app-screenshots/12-behavioral-trait-analysis.png) |

| Social story example | Visual schedule example |
|---|---|
| ![Social story example](assets/app-screenshots/20-social-story-example.png) | ![Visual schedule example](assets/app-screenshots/21-visual-schedule-example.png) |

More screenshots are available in [`assets/app-screenshots/`](assets/app-screenshots/).

## Repository structure

```text
autism-behavioral-trait-detection-agent-framework/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_qchat10_tabular_classification.ipynb
│   └── 02_bert_behavioral_text_classification.ipynb
├── results/
│   └── model_metrics.csv
├── report/
│   └── Capstone_Project_Report.pdf
├── poster/
│   └── Capstone_Project_Poster.pdf
├── presentation/
│   └── Capstone_Project_Presentation.pptx
├── assets/
│   └── app-screenshots/
└── docs/
    ├── DATASETS.md
    ├── NOTEBOOK_RUN_ORDER.md
    ├── RESULTS_AND_LIMITATIONS.md
    ├── SOURCE_AUDIT.md
    ├── AGENT_IMPLEMENTATION_SCOPE.md
    ├── CV_PROJECT_SUMMARY.md
    ├── GITHUB_UPLOAD_GUIDE.md
    └── LICENSING_AND_PUBLICATION_CHECKLIST.md
```

## How to explore or run the notebooks

1. Read [`docs/DATASETS.md`](docs/DATASETS.md) before running either notebook. The datasets are **not included** in this repository.
2. Follow [`docs/NOTEBOOK_RUN_ORDER.md`](docs/NOTEBOOK_RUN_ORDER.md).
3. Use Google Colab with a GPU for the BERT notebook. The notebooks use Colab-specific paths and `gdown` download IDs; verify the download sources and package compatibility before running.
4. The root `requirements.txt` lists the principal notebook dependencies. It is not a frozen environment lockfile, and a complete clean-room rerun has not been verified.

## Project documentation

- [Dataset provenance and access](docs/DATASETS.md)
- [Notebook run order](docs/NOTEBOOK_RUN_ORDER.md)
- [Results, limitations, and metric discrepancies](docs/RESULTS_AND_LIMITATIONS.md)
- [Source audit](docs/SOURCE_AUDIT.md)
- [Scope of supplied application source](docs/AGENT_IMPLEMENTATION_SCOPE.md)
- [CV-ready project summary](docs/CV_PROJECT_SUMMARY.md)
- [GitHub upload guide](docs/GITHUB_UPLOAD_GUIDE.md)
- [Licensing and publication checklist](docs/LICENSING_AND_PUBLICATION_CHECKLIST.md)

## Safety, ethics, and responsible use

- A prediction of “ASD” or “Non-ASD” in these datasets is a dataset label, not a clinical diagnosis.
- The report itself notes the text corpus is small and that the 14-trait extraction depends on an LLM call without sentence-level ground-truth trait labels.
- No prospective evaluation with clinicians or caregivers is included in the supplied evidence.
- Do not use the models to make diagnostic, treatment, educational-placement, or other high-stakes decisions about a child.
- Do not upload identifiable child or family information to a public notebook, public issue, third-party model, or API.

## Source artifact integrity

The two notebooks and the report/poster/presentation in this repository are copied from the supplied ZIP. The notebook files were renamed for clarity, but their internal contents were not edited. The original report is included unchanged; review [`docs/SOURCE_AUDIT.md`](docs/SOURCE_AUDIT.md) before publishing publicly because it records inconsistencies in the supplied report and presentation.
