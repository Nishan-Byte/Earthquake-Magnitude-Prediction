# Earthquake Magnitude Prediction

A machine learning project for predicting earthquake magnitude from spatial, physical, temporal, catalogue-quality, magnitude-type, and historical seismicity features.

## Overview

Earthquake magnitude is influenced by complex relationships between earthquake location, depth, catalogue characteristics, temporal patterns, and other seismicity-related information.

This project develops and evaluates multiple regression models to predict earthquake magnitude and investigates **which features contribute most strongly to the predictions** using SHAP explainability.

The final selected model is a **Tuned XGBoost Regressor**.

## Objectives

- Build a reproducible earthquake magnitude prediction pipeline.
- Engineer meaningful spatial, temporal, and historical seismicity features.
- Compare multiple regression algorithms.
- Tune the strongest tree-based models.
- Evaluate performance on an unseen chronological test set.
- Analyse prediction errors across magnitude ranges and magnitude types.
- Explain model predictions using SHAP.
- Investigate feature interactions and the effect of magnitude-type information.

## Dataset

The processed dataset contains **9,775 earthquake events**.

The target variable is:

```text
mag
