# Student Learning Engagement Analyzer

A machine-learning powered early-warning prototype that estimates a learner's
engagement risk from course interaction signals and provides actionable study
recommendations through a Streamlit interface.

> **Important:** This is an educational decision-support prototype, not a
> validated assessment of a student's ability or likelihood of success. Its
> predictions should not be used to penalize, rank, or make high-stakes decisions
> about learners.

## Features

- Accepts five engagement signals: total interactions, early interactions,
  early active days, first activity day, and pre-course engagement.
- Loads a trained classification model and estimates risk probability.
- Converts the probability into Low, Medium, or High risk bands.
- Generates rule-based observations and suggested next steps.
- Displays a simple explanation of the decision-tree path.
- Provides an interactive Streamlit application.

## Project structure

```text
.
├── config/
│   └── config.yaml
├── core/
│   ├── feature_builder.py
│   ├── predictor.py
│   └── recommender.py
├── models/
│   └── artefacts/
│       └── finalized_model.joblib
├── research/
│   └── notebooks/
│       ├── N1_Data_Understanding_and_Memory-Safe_Loading.ipynb
│       ├── N2_Engagement_Understanding_and_Target_Design.ipynb
│       ├── N3_Temporal_Engagement_and_Early_Signals.ipynb
│       └── N4_Engagement-Aware_Recommendation_System.ipynb
├── utils/
│   ├── model_loader.py
│   ├── path_utils.py
│   └── validators.py
├── main.py
├── streamlit_app.py
└── requirements.txt
```

## Tech stack

- Python 3.12
- Pandas and NumPy
- Scikit-learn
- Joblib
- Streamlit
- PyYAML
- Jupyter Notebook (for research and experimentation)

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/student-learning-engagement-analyzer.git
cd student-learning-engagement-analyzer
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

macOS / Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit application

```bash
streamlit run streamlit_app.py
```

Open the local URL printed by Streamlit in your browser.

### Optional: run the command-line example

```bash
python main.py
```

## Model inputs

| Feature | Meaning |
|---|---|
| `total_click` | Total learning interactions during the course |
| `early_click` | Interactions during the early course period |
| `early_active_days` | Number of distinct active days in the early period |
| `first_activity_day` | Days from course start to first activity; negative values indicate pre-course activity |
| `pre_course_engaged` | Whether the learner interacted before the official course start (0 or 1) |

## Risk bands

The current application uses the following probability thresholds, configured in
`config/config.yaml`:

- **Low:** probability below 0.40
- **Medium:** probability from 0.40 to below 0.70
- **High:** probability at least 0.70

These are prototype thresholds and should be calibrated and evaluated on
appropriate held-out data before real-world use.

## Research notebooks

The notebooks document the project workflow:

1. Data understanding and memory-safe loading
2. Engagement feature understanding and target design
3. Temporal engagement and early-warning signals
4. Engagement-aware recommendation system

The notebooks are included without saved cell outputs. The source datasets are
not included, so reproduce the experiments only after obtaining the appropriate
dataset and updating the notebook data paths.

## Data privacy

Raw student-level CSV files and source datasets are intentionally excluded.
Do not commit identifiable student records, private datasets, credentials,
tokens, or other confidential information. Confirm that you have permission to
redistribute any dataset or model artifact before publishing.

## Limitations and responsible use

- Model performance metrics and external validation results are not currently
  reported in this repository.
- Risk predictions depend on the training data and feature definitions.
- Recommendations are rule-based and are not a substitute for instructor support.
- Check for bias and differences in model performance across learner groups
  before any real-world deployment.

## Future improvements

- Add unit tests and input-range validation.
- Report held-out evaluation metrics and calibration.
- Add model versioning and reproducible training instructions.
- Improve explanations and recommendation personalization.
- Add accessibility and usability tests for the Streamlit interface.

## Acknowledgements

This repository contains the application code, trained model artifact, and
research notebooks supplied for this project. Add dataset and source
acknowledgements here once their exact provenance and license are confirmed.
