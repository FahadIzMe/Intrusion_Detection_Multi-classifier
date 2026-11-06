# Intrusion_Detection_Multi-classifier
- Trained multiple classifiers on the large multiclass CIC-IDS2017 network intrusion dataset. The purpose was to demonstrate the handling of large datasets that do not fit in memory.
- Used under-sampling and SMOTE to handle the large imbalance and size of data.
- Use agents for the project as instructed by our professor.

## Table of Contents

- [Tools](#tools)
- [Summary](#summary)
- [Credits](#credits)

## Tools
- Python

## Summary
- Dataset Summary:
  Total Samples: 2,793,860
  Features: 78
  Attack Types: 15
  Training Samples (after SMOTE): 2,228,284
  Test Samples: 565,576

- Models Trained:
  1. Random Forest
  2. XGBoost
  3. LightGBM
  4. Logistic Regression
  5. Neural Network

- Best Performing Model:
  Model: XGBoost
  Accuracy: 0.9984
  Precision: 0.9987
  Recall: 0.9984
  F1-Score: 0.9985


## Credits
- Dataset is the public CIC-IDS2017 network intrusion dataset.
