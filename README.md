# Freight Rate Prediction

## About the Project
This project predicts freight rates for truck shipments using machine learning. The goal was to train a model on historical shipment data and generate predictions for unseen loads.

## Dataset
The dataset contains shipment information such as:
- Pickup and delivery locations
- Distance and equipment type
- Shipment weight and date
- Market index and quote signal
- Posted freight rate (target variable)

## Approach
1. Explored the dataset and checked missing and invalid values.
2. Used a chronological train-validation split to train on earlier months and validate on October 2025.
3. Prepared the features, including date-based features and categorical columns.
4. Trained a CatBoost regression model and evaluated its performance.
5. Generated predictions for the validation dataset and December 2025 inputs.
6. Ran the provided scoring script to validate the output files and generate the December prediction chart.

## Model Evaluation
The best experiment so far used a log-transformed target with CatBoost.

| Metric | Result |
|---|---:|
| MAE | 108.21 |
| RMSE | 647.71 |
| R² | 0.8204 |

These metrics are from the October 2025 holdout set. They should not be interpreted as final test-set performance.

## Project Files
- `notebooks/freight_rate_model.ipynb` — data exploration, training and predictions
- `outputs/validation_predictions.csv` — predictions for the validation dataset
- `outputs/december_predictions.csv` — December 2025 predictions
- `scorer_results/candidate_december.png` — December prediction chart
- `score.py` — provided validation and chart-generation script
- `requirements.txt` — required Python libraries

## How to Run
Install the dependencies:

```bash
pip install -r requirements.txt
```

Run the notebook in Google Colab or Jupyter after placing the required input CSV files in the expected location.

To validate the generated outputs, run:

```bash
python score.py --predictions outputs/validation_predictions.csv --december-predictions outputs/december_predictions.csv --output-dir scorer_results
```

Update the file paths if your CSV files are stored elsewhere.

## Notes
The December dataset does not include all the features available in the main training dataset, so a separate model using the shared features was trained for December predictions.

This project was completed as a freight-rate machine learning assessment.
