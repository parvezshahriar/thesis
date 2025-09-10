# Diabetes Prediction Web App

## Repository Structure
```
.
├── diabetes.csv                  # Dataset used for training/analysis
├── trained_model.sav            # Serialized model (pickle/joblib)
├── requirements.txt             # Python dependencies
└── Diabetes Prediction web app.py # Main web app script
```

## Quickstart
1. Clone the repository:
   ```bash
   git clone https://github.com/parvezshahriar/thesis.git
   cd thesis
   ```

2. Set up and install:
   ```bash
   python -m venv venv
   source venv/bin/activate    # or venv\Scripts\activate on Windows
   pip install -r requirements.txt
   ```

3. Run the app. Because the filename has spaces, use quotes:
   ```bash
   python "Diabetes Prediction web app.py"
   ```
   Or, if the script is a Streamlit app:
   ```bash
   streamlit run "Diabetes Prediction web app.py"
   ```

4. Run the app (common options):
   Confirm which framework the app uses by inspecting the top of the Python file:
   - `import streamlit as st` → Streamlit
   - `from flask import Flask` → Flask
   - `import tkinter` → Desktop GUI

   **Flask:**
   ```bash
   python "Diabetes Prediction web app.py"
   ```

   **Streamlit:**
   ```bash
   streamlit run "Diabetes Prediction web app.py"
   ```

## How It Works (High Level)
- The app loads `trained_model.sav` using pickle or joblib.
- The UI collects the required input features from the user (see `diabetes.csv` for feature names and ordering).
- Inputs are preprocessed into the same numeric array shape the model expects.
- The model returns a prediction (class/probability), and the UI shows the result.

## Development Suggestions
- Rename `Diabetes Prediction web app.py` to `app.py` or `diabetes_app.py` to avoid quoting issues.
- Add `.gitignore` to exclude virtual environments and `__pycache__/`.
- Add logging and input validation to the web app to handle bad inputs gracefully.
- Separate model and app code into modules (`model.py` and `app.py`).
- Add tests for input preprocessing and prediction outputs.

## Security & Privacy Notes
- Do not load model files from untrusted sources — pickle/joblib can execute code when loaded.
- If using real patient data, follow applicable privacy laws (HIPAA, GDPR, local regulations).
- If deployed publicly, secure the endpoint (authentication, rate limiting, input validation) and avoid exposing the raw trained model file.