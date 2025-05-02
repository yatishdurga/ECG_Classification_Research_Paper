# 🩺 ECG-Based Arrhythmia Detection Using R-Peak Features and Machine Learning

This repository contains an end-to-end pipeline for detecting cardiac arrhythmias using Electrocardiogram (ECG) signals from the MIT-BIH Arrhythmia Dataset. The approach leverages signal processing, HRV feature extraction, and machine learning models (Random Forest and XGBoost) to classify heartbeats into different types (Normal, Ventricular, Supraventricular, etc.).

---

## 📁 Dataset

- **Source:** [MIT-BIH Arrhythmia Database on PhysioNet](https://physionet.org/content/mitdb/1.0.0/)
- **Records Used:** 25 ECG records sampled at 360 Hz, each 30 minutes long.
- **Annotations Included:** N (Normal), V (Ventricular), S (Supraventricular), F (Fusion), Q (Unknown).

---

## 🧠 ML Workflow Overview

1. **Signal Preprocessing**
   - Applied 0.5–50 Hz Butterworth bandpass filter.
   - Removed noise and baseline drift.

2. **R-Peak Detection**
   - Used `NeuroKit2`'s Pan-Tompkins algorithm.

3. **HRV Feature Extraction**
   - Extracted RR intervals and time-domain HRV metrics using `nk.hrv()`.

4. **Data Labeling**
   - Matched annotated beats (within ±50 ms) to detected R-peaks.

5. **SMOTE Balancing**
   - Applied SMOTE to handle class imbalance in labeled beats.

6. **Model Training**
   - Trained and evaluated `RandomForestClassifier` and `XGBoostClassifier`.

7. **Model Evaluation**
   - Accuracy, Precision, Recall, F1-score, Confusion Matrix, ROC-AUC.

---

## 🛠 Tech Stack

- Python 3.10+
- Libraries: `wfdb`, `neurokit2`, `scikit-learn`, `xgboost`, `matplotlib`, `seaborn`, `imblearn`
- Dataset: MIT-BIH Arrhythmia
- Environment: Jupyter Notebook or Google Colab

---

## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ecg-arrhythmia-detection.git
cd ecg-arrhythmia-detection
