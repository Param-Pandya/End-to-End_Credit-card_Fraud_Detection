# 💳 Credit Risk Prediction API

A Flask-based Machine Learning API that predicts whether a loan applicant is likely to **pay back** or **default**, based on the German Credit dataset. The model is trained using `XGBoost` and served as a REST API using `Flask`.

---

## 🚀 Features

- Train a credit risk classification model using the German Credit dataset.
- REST API with:
  - `GET /` — simple homepage.
  - `GET /predict` — provides API usage instructions.
  - `POST /predict` — returns credit risk prediction and confidence score.
- Preprocessing with `ColumnTransformer` and `OneHotEncoder`.
- Model persistence via `joblib`.

---

## 🧠 Tech Stack

- **Backend**: Flask
- **ML Model**: XGBoost
- **Data Processing**: Pandas, Scikit-learn
- **Visualization**: Matplotlib (used in notebook)
- **Serialization**: Joblib

---

## 📁 File Structure

```
.
├── main.py                   # Flask API for serving predictions
├── loan_payback.ipynb       # Training notebook using GermanCredit dataset
├── creadit_pipeline.pkl     # Saved ML pipeline (generated after training)
├── test_payloads.json       # Sample test payloads for API testing
├── requirements.txt         # Python dependencies
├── GermanCredit.csv         # Dataset (not included here)
└── README.md                # Project documentation (this file)
```

---

## ⚙️ Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/credit-risk-api.git
   cd credit-risk-api
   ```

2. **Create a virtual environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

---

## 📊 Model Training (Optional)

Run the training notebook:

```bash
jupyter notebook loan_payback.ipynb
```

This notebook will:
- Load and preprocess the data.
- Train an XGBoost classifier.
- Evaluate the model.
- Save the trained pipeline as `creadit_pipeline.pkl`.

---

## 🧪 Running the API

Make sure `creadit_pipeline.pkl` is present in the root directory.

```bash
python main.py
```

The Flask server will start at `http://0.0.0.0:5000`.

---

## 🔁 API Endpoints

### `GET /`
Returns a simple homepage for KimJerry AI Lab.

---

### `GET /predict`
Returns an example of how to format your JSON POST payload.

#### Response:
```json
{
  "message": "Please send a POST request to this endpoint with a JSON body to get the prediction",
  "example_payload": {
    "status": "no_checking_account",
    "duration": 60,
    ...
  }
}
```

---

### `POST /predict`

Send one or more records in JSON format to get predictions.

#### Example:
```json
[
  {
    "status": "no_checking_account",
    "duration": 60,
    "credit_history": "critical_account_other_credits_existing",
    "purpose": "retraining",
    "amount": 10000,
    ...
  }
]
```

#### Response:
```json
[
  {
    "confidence": "92.13%",
    "outcome": "Likely to default (not pay back)"
  },
  {
    "confidence": "88.44%",
    "outcome": "Likely to pay back"
  }
]
```

---

## 📦 Sample Test Payloads

Use the `test_payloads.json` file to test multiple inputs in Postman or cURL.

---

## 📌 Notes

- The model outputs binary classification:
  - `0` = Likely to pay back
  - `1` = Likely to default
- Confidence score is based on class probability.

---

## 🪪 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

---

## 👨‍💻 Author

Made with ❤️ by Param Pandya

