# MLPRCDAproject

# Sleep-HRV Interaction Analysis Using Wearable Data

This project analyzes the relationship between sleep metrics collected from wearable data and next-day heart rate variability (HRV). The main goal was to see which sleep metric is most informative for next-day HRV.

The required input variables were:

- deep sleep duration
- REM sleep duration
- sleep efficiency

The target variable was next-day HRV measured in milliseconds.

## Project idea

Heart rate variability is often used as an indicator of recovery, stress and autonomic nervous system activity. Since sleep is closely related to recovery, this project checks whether wearable sleep metrics can help explain or predict next-day HRV.

The project is not meant to be a clinical prediction system. The data come from a wearable device, so the results should be interpreted as exploratory findings. The analysis shows patterns in the available data, but it does not prove that one sleep metric causes changes in HRV.

## Data

The project uses wearable health data from three CSV files:

- Vital Signs
- Sleep
- Activity

The sleep data were aggregated by wake-up date. Vital signs were merged by date and previous-day activity was aligned with next-day HRV. The final dataset was created at the daily level, where one row represents one sleep-HRV observation.

## Workflow

The project includes two main parts.

### Computational Data Analytics

This part focuses on preparing and understanding the data. It includes:

- loading wearable CSV files
- checking data types and missing values
- converting percentage values to numeric format
- aggregating sleep records by wake-up date
- merging sleep, vital signs and activity data
- checking duplicates
- outlier analysis using IQR and Z-score methods
- descriptive statistics
- time-series plots
- histograms and scatter plots
- Pearson correlation analysis
- KMeans sleep-profile clustering

### Machine Learning and Pattern Recognition

This part focuses on modelling and validation. Each daily record is treated as a pattern represented by sleep-related features.

The main task is regression because next-day HRV is a continuous target. The models used include:

- baseline mean regression
- linear regression
- ridge regression
- KNN regression
- decision tree regression
- random forest regression

The final model was selected using validation RMSE and then tested on unseen future data.

The project also includes an optional low-HRV classification extension to cover additional pattern recognition methods such as:

- KNN classifier
- Gaussian Naive Bayes
- decision tree classifier
- MED nearest-prototype classifier
- Gaussian maximum likelihood classifier
- Gaussian MAP classifier

## Validation

Since the data are ordered by date, random splitting was avoided. A temporal train-validation-test split was used so that future observations were not mixed into training.

A 5-fold time-series cross-validation was also included as an additional robustness check.

## Explainability

Feature influence was analyzed using:

- Pearson correlation
- standardized linear regression coefficients
- permutation importance
- single-feature models

Permutation importance was used to understand how much the selected model depends on each sleep metric. This explains model behaviour, not biological causality.

## Main finding

The model did not generalize well enough to be used as a reliable clinical prediction tool. The most useful part of the project is the exploratory analysis and feature influence interpretation.

Among the required sleep metrics, deep sleep duration was identified as the most informative feature in the combined influence analysis.

## Files in this repository

The repository contains:

- Jupyter notebook with the full analysis
- cleaned output CSV files
- generated figures
- project report
- project poster
- README file

## How to run the notebook

1. Open the notebook in Google Colab or Jupyter Notebook.
2. Upload the required CSV files or place them in the same folder as the notebook.
3. Run the cells from top to bottom.
4. Generated figures and output files will be saved automatically.

The notebook uses Python libraries such as:

- pandas
- NumPy
- matplotlib
- scikit-learn

## Notes

The results should be interpreted carefully because the dataset is limited in size and comes from a wearable device. Wearable sleep-stage estimates can contain measurement noise. The analysis is observational, so it shows associations and prediction patterns rather than causal effects.
