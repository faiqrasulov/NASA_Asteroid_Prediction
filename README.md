# Hazardous asteroid classification with XGBoost

> Course assignment from 2023, kept as it was written. The notes under "Reading the result" were added in November 2026.

Classifies near-Earth asteroids as hazardous or not from NASA NeoWs data (4,687 records, 755
hazardous) with XGBoost, tuned with Bayesian optimisation (`BayesSearchCV`).

## Result

On the 938 test records the default XGBoost model and the tuned one both score 1.00 accuracy;
precision and recall for the hazardous class are 0.99-1.00.

## Reading the result

- **The score is this high because the label is a rule.** NASA calls an asteroid potentially
  hazardous when its minimum orbit intersection distance is at most 0.05 au and its absolute
  magnitude is at most 22. Both quantities are columns in the data, so a tree model recovers the
  rule. The task checks that a pipeline works; it is not a prediction problem.
- The 4,687 records describe 3,692 asteroids. Some asteroids are in both the training and the
  test set.
- Tuning could not help a model that already scores 1.00, and it did not.

## Newer work on the same topic

- [anomaly-detection-benchmark](https://github.com/faiqrasulov/anomaly-detection-benchmark): rare-event detection where the answer is not in the features, scored by precision-recall.

## Files

| File | Content |
|---|---|
| `NASA_Asteroid_Prediction.ipynb` | Analysis |
| `NASA_Asteroid_Prediction.html` | Rendered copy |
| `nasa.csv` | The dataset ([Kaggle](https://www.kaggle.com/shrutimehta/nasa-asteroids-classification)) |
| `About.txt` | Original brief |
