# Copilot Instructions for AI Coding Agents

## Project Overview
- **Purpose:** Predict customer churn for a telecommunications company using a logistic regression model (scikit-learn) trained on the IBM Telco Customer Churn dataset.
- **Key Components:**
  - `notebooks/telco_marimo.py`: Model training and experimentation (Marimo framework).
  - `models/`: Stores serialized models (joblib format).
  - `prediction.py`: Loads the model and provides a prediction interface.
  - `tests/`: Contains test cases (pytest).
  - `input/`: Raw data (CSV).

## Data Flow & Architecture
- Data is loaded from `input/WA_Fn-UseC_-Telco-Customer-Churn.csv`.
- Model is trained in the notebook, then saved to `models/telco_logistic_regression.joblib`.
- `prediction.py` loads the model and exposes a `make_prediction` function for inference.
- Tests in `tests/test_prediction.py` validate prediction logic.

## Developer Workflows
- **Run tests:** `pytest` from the project root.
- **Retrain model:** Edit and run `notebooks/telco_marimo.py`.
- **Update model:** Overwrite the model file in `models/` after retraining.
- **Prediction example:** See `prediction.py` for usage.

## Conventions & Patterns
- Only three features are used by default: `tenure`, `MonthlyCharges`, `TechSupport_yes`.
- Model and scaler are bundled together using joblib.
- All new features or model changes should be reflected in both the notebook and `prediction.py`.
- Tests should cover both typical and edge-case predictions.

## Integration & Deployment
- **Azure Functions:**
  - Use the Azure Functions extension for deployment (see README for step-by-step guide).
  - Expose prediction via HTTP trigger, mapping request params to model features.
  - Update workflow YAMLs as described in the README for serverless deployment.

## Examples
- **Prediction call:**
  ```python
  prediction = make_prediction(tenure=12, MonthlyCharges=70.5, TechSupport_yes=1)
  ```
- **Test run:**
  ```bash
  pytest
  ```

## References
- See `README.md` for full deployment and CI instructions.
- Example model usage and feature mapping in `prediction.py` and Azure Function notes in README.
