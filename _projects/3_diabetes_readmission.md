---
layout: page
title: Diabetes Readmission Prediction
description: Predicting 30-day hospital readmission — logistic baseline to XGBoost to a tabular transformer, with SHAP
img: assets/img/projects/diabetes.png
importance: 3
category: ""
---

**The problem.** Hospital readmissions within 30 days are costly and often preventable. Using the UCI "Diabetes 130-US hospitals" dataset (1999–2008, ~100k encounters), we built and compared models to flag diabetic patients at high readmission risk — UC Berkeley MIDS Applied Machine Learning final project.

<div class="row justify-content-center">
    <div class="col-sm-10 mt-3 mb-3">
        {% include figure.liquid loading="eager" path="assets/img/projects/diabetes.png" title="Model comparison" class="img-fluid rounded z-depth-1" %}
</div>
</div>
<div class="caption">
    Model comparison across the four architectures. Class imbalance made accuracy misleading, so F1 drove model selection.
</div>

**How it works.** A shared preprocessing pipeline (cleaning, encoding, VIF-screened features) feeds four models: a logistic regression baseline, random forest, XGBoost, and a Keras tabular transformer tuned with Keras Tuner. The raw class balance produced near-zero F1 with deceptively high accuracy, so we rebalanced training data (SMOTE/oversampling to ~51/49) and evaluated on F1. SHAP explains the final model's drivers, and we checked subgroup performance (e.g., F1 59.8% female vs. 55.8% male) rather than reporting a single blended number.

**Results.** XGBoost won: F1 57.91% and test accuracy 56.47%, with random forest close behind (57.56% / 56.31%) but overfitting; the transformer underperformed on this tabular problem. Modest absolute scores are the honest headline — the report discusses why (label noise, temporal boundary of the data) and what a hospital deployment would need.

**My role.** Data preparation and the visualization + transformer workstream, with the team: Terra Jiang, Sai Sriya Mudigonda, and Rahil Sharma.

**Links.** [Repository](https://github.com/cpfrish/diabetes-readmission) — includes the full proposal → milestone → report → slides chain.
