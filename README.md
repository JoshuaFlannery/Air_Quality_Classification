[View Full Report](https://joshuaflannery.github.io/Air_Quality_Classification/)

# Air Quality Classification

## Overview

This project applies machine learning techniques to classify air quality into four categories: Good, Moderate, Poor, and Hazardous. Multiple models are developed and compared, including Support Vector Machines (SVM) with different kernels and a Random Forest model, to evaluate performance across varying levels of model complexity.

The goal is to assess classification performance and understand how feature relationships influence predictive accuracy.

------------------------------------------------------------------------

## Dataset

The dataset consists of approximately 5,000 observations with 9 numeric predictor variables related to environmental and pollution measurements. The target variable, **Air.Quality**, contains four categorical classes.

Key characteristics: - No missing values - Moderate class imbalance (Good most frequent, Hazardous least frequent) - High correlation between PM2.5 and PM10 (\~0.97) - Variables operate on different scales

------------------------------------------------------------------------

## Methodology

### Data Preparation

-   Stratified 80/20 train-test split to preserve class distribution
-   Feature standardization applied to SVM models using training data only (to prevent data leakage)
-   Random Forest trained on unscaled data

### Models

-   **Support Vector Machines (SVM)**
    -   Linear kernel
    -   Polynomial kernel
    -   Radial kernel
-   **Random Forest**

### Model Training

-   SVM models tuned using cross-validation over kernel-specific hyperparameters
-   Random Forest tuned over multiple values of the feature-sampling parameter (`mtry`) using 10-fold cross-validation
-   Performance evaluated on a held-out test set

------------------------------------------------------------------------

## Results

| Model          | Accuracy |
|----------------|----------|
| Linear SVM     | 0.947    |
| Polynomial SVM | 0.933    |
| Radial SVM     | 0.949    |
| Random Forest  | 0.961    |

-   All models achieved high accuracy
-   Random Forest performed best, though improvement over SVM was modest
-   Confusion matrices highlight variation in class-level performance
-   Feature importance identifies key predictors influencing classification

------------------------------------------------------------------------

## Key Findings

-   **Model Performance**
    -   Linear and radial SVM models performed similarly, suggesting largely linear separability
    -   Random Forest provided a slight performance improvement, capturing additional nonlinear relationships
-   **Feature Relationships**
    -   CO and proximity to industrial areas were the most influential predictors
    -   PM2.5 and PM10 showed high correlation but lower importance in classification
-   **Class Behavior**
    -   Strong separation exists for low pollution levels (Good category)
    -   Overlap between adjacent categories (Moderate and Poor) contributes to classification difficulty

------------------------------------------------------------------------

## Conclusion

All models performed well, with Random Forest achieving the highest accuracy. However, the small performance gap indicates that simpler models such as linear SVM can be effective for this dataset.

Feature importance analysis highlights that air quality classification is driven primarily by CO levels and environmental proximity factors, rather than particulate measures alone.

------------------------------------------------------------------------

## Tools & Libraries

-   R
-   caret
-   e1071
-   randomForest
-   knitr

------------------------------------------------------------------------

## Project Structure

-   `Air Quality Classification.qmd` – Main analysis and report
-   `air_quality.csv` – Dataset used for modeling
-   `index.html` – Rendered report (viewable without running code)
