---
layout: post
title: Cross-validation and resampling for heavily imbalanced data
---

The [credit card fraud detection](https://www.kaggle.com/mlg-ulb/creditcardfraud) data set on Kaggle is a great example of a heavily imbalanced data set. In [this kaggle notebook](https://www.kaggle.com/lane203j/auprc-5-fold-c-v-and-resampling-methods/notebook), I demonstrate how to properly evaluate a classification model for imbalanced using:

- area under the precision-recall curve (AUPRC) as the metric
- 5-fold cross-validation 
- random oversampling and other oversampling techniques like SMOTE

The notebook also highlights several common mistakes in other kernels:

- Not using AUPRC
- Performing over/under sampling before cross-validation splits
- Performing feature selection before cross-validation splits
- Not using stratified k-fold splits

For the sake of example, the notebook evaluates a logistic regression model. The code is flexible so that you can replace logistic regression with any other scikit or scikit-wrapped model and run the same evaluation.
