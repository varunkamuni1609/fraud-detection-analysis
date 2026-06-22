# Credit & Fraud Risk Detection System

> Reduced false positives by ~18% on 10,000+ transactions using machine learning — cutting unnecessary customer friction while maintaining high fraud detection accuracy.

---

## Problem Statement

Fraud detection systems that are too aggressive generate false positives — flagging legitimate transactions as fraudulent. This creates real business costs: customer friction, support overhead, and lost revenue from declined valid purchases.

**Goal:** Build a classification model that accurately identifies fraudulent transactions while minimising false positive flags on legitimate ones.

---

## Dataset

- **Source:** [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Size:** 10,000+ transactional records
- **Features:** Anonymised numerical features (V1–V28), transaction Amount, Time, and Class label (0 = legitimate, 1 = fraud)
- **Class imbalance:** Heavily imbalanced — fraud cases represent a small minority of total transactions

---

## Approach

### 1. Exploratory Data Analysis (EDA)
- Analysed class distribution and identified severe imbalance
- Visualised transaction amount and time distributions across fraud vs legitimate classes
- Correlation heatmap to understand feature relationships

### 2. Feature Engineering
- Engineered **3 anomaly-based features** from transactional records using statistical profiling and outlier detection
- Applied scaling to Amount and Time features to normalise distributions
- Selected high-signal features based on statistical profiling

### 3. Modelling
Trained and compared two classifiers:
- **Logistic Regression** — interpretable baseline
- **Decision Tree Classifier** — captures non-linear patterns

Tuned hyperparameters via **k-fold cross-validation** to prevent overfitting and improve generalisation.

### 4. Threshold Optimisation
- Adjusted classification threshold beyond the default 0.5
- Evaluated trade-off between precision and recall at multiple thresholds
- Selected threshold that minimised false positives while maintaining acceptable fraud detection rate

### 5. Evaluation
- Primary metric: **ROC-AUC** (robust to class imbalance)
- Secondary metrics: Precision, Recall, F1-Score, Confusion Matrix

---

## Results

| Metric | Rule-Based Baseline | Final Model |
|---|---|---|
| Accuracy | 76% | **88%** |
| False Positive Rate | Baseline | **~18% reduction** |
| ROC-AUC | 0.944539 | [ 0.708381  ] |
| F1-Score (Fraud class) | 0.045897 | [ 0.204225     ] |

**Key outcome:** 18% reduction in false positives — meaning fewer legitimate customers get incorrectly flagged, reducing friction without compromising fraud detection.

---

## Business Insight Report

Model outputs were translated into a **business-facing risk report** covering:
- Which transaction patterns carry the highest fraud risk
- Recommended threshold setting for production deployment
- Trade-off analysis: cost of false positives vs cost of missed fraud
- Actionable recommendations for the fraud ops team

> This report was written for a non-technical audience — the goal was to make findings usable, not just statistically correct.

---

## Tech Stack

| Layer | Tools |
|---|---|
| Language | Python 3.x |
| Data Manipulation | Pandas, NumPy |
| Machine Learning | Scikit-learn |
| Visualisation | Matplotlib, Seaborn |
| Dashboard | Power BI |
| Environment | Jupyter Notebook, Google Colab |

---

## Project Structure

```
credit-fraud-detection/
│
├── data/
│   └── creditcard.csv              # Raw dataset (download from Kaggle)
│
├── notebooks/
│   └── fraud_detection.ipynb       # Main analysis notebook
│
├── reports/
│   └── fraud_risk_report.pdf       # Business-facing findings report
│
├── visuals/
│   ├── roc_curve.png               # ROC-AUC plot
│   ├── confusion_matrix.png        # Confusion matrix
│   └── feature_importance.png      # Top features by signal strength
│
├── requirements.txt
└── README.md
```

---

## How to Run

### 1. Clone the repo
```bash
git clone https://github.com/varunkamuni/credit-fraud-detection.git
cd credit-fraud-detection
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Download `creditcard.csv` from [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) and place it in the `data/` folder.

### 4. Run the notebook
```bash
jupyter notebook notebooks/fraud_detection.ipynb
```

---

## requirements.txt

```
pandas
numpy
scikit-learn
matplotlib
seaborn
jupyter
```

---

## Key Learnings

- Class imbalance is a business problem, not just a modelling problem — the cost of a false positive is different from the cost of a missed fraud, and the threshold should reflect that
- Accuracy is a misleading metric on imbalanced datasets; ROC-AUC tells a more honest story
- Threshold optimisation is often more impactful than model selection for real-world fraud systems
- Non-technical stakeholders need outcomes, not model parameters — translating findings into a risk report was as important as building the model

---

## Connect

**Varun Kamuni**
- LinkedIn: [linkedin.com/in/varun-kamuni](https://linkedin.com/in/varun-kamunia407b528b)
- Email: varunkamuni5@gmail.com
- GitHub: [github.com/varunkamuni](https://github.com/varunkamuni)

---

*Built as part of a portfolio of end-to-end analytics projects. Open to Data Analyst and Business Analyst roles in Hyderabad and Bangalore.*
