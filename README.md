# Intrusion_Detection_Multi-classifier

This repository contains a multiclass CICIDS2017 intrusion-detection workflow. It loads the dataset CSVs, removes exact duplicates, cleans invalid rows, splits the data, applies under-sampling and SMOTE to training data only, compares four classifiers by macro F1, and saves the best model.

I have updated this repository to remove the patchwork and overengineering from the previous version, which came from my initial focus on getting it to run successfully. I am treating this version as an ongoing practice project to improve my skills by focusing on core concepts rather than fluff.

Previously, instead of paying attention to the classes with low amounts of records, I had been focusing on the overall non-weighted accuracy. This time I am correcting that mistake and focusing on the smaller classes that don't have enough data. Later on, I will focus on balancing these classes better.

The project used agents as instructed by our professor.


## Table of Contents

- [Tools](#tools)
- [Dataset and preprocessing](#dataset-and-preprocessing)
- [Models](#models)
- [Best model results](#best-model-results)
- [Running locally](#running-locally)
- [Credits](#credits)

## Tools
- Python

## Dataset and preprocessing

The notebook processes the eight CICIDS2017 CSV files in `CIC_IDS2017/`.

- Source CSV rows: 2,830,743
- Exact duplicate rows removed: 308,387
- Rows after deduplication: 2,522,356
- Rows retained after numeric and label cleaning: 2,520,792
- Features: 78
- Classes: 15, including BENIGN
- Training rows before balancing: 2,016,633
- Untouched test rows: 504,159
- Training rows after under-sampling and SMOTE: 2,023,822

The stratified train/test split happens before resampling. The test set is not resampled. BENIGN training rows are under-sampled, and SMOTE is applied to eligible minority classes.

## Models

Four classifiers are compared using macro F1:

1. Logistic Regression
2. Random Forest
3. XGBoost
4. LightGBM

| Model | Macro F1 |
| --- | ---: |
| XGBoost | 0.880205 |
| Random Forest | 0.812855 |
| Logistic Regression | 0.510844 |
| LightGBM | 0.168876 |

## Best model results

XGBoost was selected by macro F1 and evaluated on the untouched test set.

- Accuracy: 0.99776261
- Weighted precision: 0.99853862
- Weighted recall: 0.99776261
- Weighted F1: 0.99804036
- Macro F1: 0.88020529

The notebook saves the best model, scaler, label encoder, and feature-column list to `models/best_intrusion_detection_model.joblib`.

## Running locally

Install the notebook dependencies in your Python environment:

```text
numpy
pandas
scikit-learn
imbalanced-learn
lightgbm
xgboost
joblib
```

Place the CICIDS2017 CSV files in `CIC_IDS2017/`, then run `intrusion-detection-system-smote-no-neural-network.ipynb`. The notebook creates the `models/` directory when saving the best model.

## Credits

The dataset is the public CICIDS2017 network intrusion dataset.
