# AMR Forecasting using XGBoost

## Project Overview

This project focuses on predicting **Antimicrobial Resistance (AMR)** using machine learning.  
An **XGBoost classification model** was developed to predict whether bacterial samples are **resistant or susceptible** to antibiotics based on genomic and MIC (Minimum Inhibitory Concentration) data.

The workflow includes data cleaning, MIC processing, feature engineering, leak-safe encoding, model training, threshold tuning, and evaluation.

---

## Dataset Processing

The raw dataset contained missing values, inconsistent MIC formats, and duplicate entries. The following preprocessing steps were performed:

- Parsed and cleaned **MIC values**
- Converted MIC values into numeric format
- Applied **log transformation** to MIC values
- Created **MIC presence indicators**
- Rescued missing resistance labels using MIC thresholds
- Removed duplicate rows
- Dropped unnecessary columns
- Handled categorical features using **5-fold leak-safe target encoding**

---

## Feature Engineering

New features were created to improve model learning, including:

- `mic_value` — cleaned numeric MIC value  
- `mic_log` — log-transformed MIC value  
- `has_mic` — MIC availability indicator  
- `ab_resistance_rate` — resistance rate per antibiotic  
- `taxon_ab_resistance_rate` — resistance rate per taxon-antibiotic pair  
- `genus_ab_resistance_rate` — resistance rate per genus-antibiotic pair  

These engineered features helped capture historical resistance patterns.

---

## Model Training

The dataset was divided into:

- Training Set
- Validation Set
- Test Set

An **XGBoost classifier** was trained using:

- Early stopping
- Cross-validation encoding
- Threshold tuning

Threshold tuning was used to determine the optimal classification cutoff instead of using the default value.

---

## Model Performance

Final evaluation metrics:

- **Validation AUC:** ~0.886  
- **Test AUC:** ~0.889  
- **Weighted F1 Score:** ~0.798  
- **Optimal Threshold:** ~0.53  

The model demonstrated strong performance in predicting antimicrobial resistance.

---

## Files Included

This repository contains:

- `XGBoost_Model_File.ipynb` — Full model development notebook  
- `model.joblib` — Trained XGBoost model  
- `encoder.joblib` — Target encoding object  
- `requirements.txt` — Required Python libraries  
- `README.md` — Project documentation  

---


**Project video:**
https://www.loom.com/share/cc71164456be49d5925b4d6f4e031d3b

**Technologies Used**
Python
Pandas
NumPy
Scikit-learn
XGBoost
Joblib
