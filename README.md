# Weather-Prediction
End-to-end weather prediction project using Python, XGBoost and GridSearchCV. Built a complete ML workflow covering data preprocessing, feature engineering, model training and optimisation, improving prediction accuracy from 76.8% to 80.9%.

Seattle Weather Classification & Next-Day Prediction

Project Overview

This project uses machine learning on historical Seattle weather data to address two related problems:

* Same-day weather classification: classify weather conditions using precipitation, temperature, and wind measurements.
* Next-day weather prediction: predict the following day’s weather using only information from previous days.

The project demonstrates a complete machine learning workflow, including data preparation, exploratory analysis, feature engineering, model development, class imbalance handling, hyperparameter optimisation, model evaluation, and time-based forecasting.

---

Project Objectives

* Analyse historical weather patterns.
* Build machine learning models for weather classification.
* Compare XGBoost, Random Forest and baseline models.
* Handle imbalanced weather classes such as drizzle, fog and snow.
* Optimise model performance using GridSearchCV.
* Evaluate models using metrics beyond headline accuracy.
* Develop a realistic next-day forecasting model that prevents data leakage.

---

Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* XGBoost
* Random Forest
* GridSearchCV
* Jupyter Notebook

---

Machine Learning Workflow

1. Data Exploration

The dataset was reviewed for data quality, weather class distribution, and patterns in precipitation, maximum and minimum temperature, and wind speed.

Exploratory analysis revealed significant class imbalance, with rain and sun occurring much more frequently than drizzle, fog, and snow.

2. Data Preparation

The weather target was converted to numerical labels, and key numerical features were prepared for modeling.

For same-day classification, a stratified train-test split maintained the distribution of weather classes in both training and testing datasets.

3. Baseline XGBoost Model

XGBoost was selected as the initial classification model for its ability to capture complex relationships in structured data.

The baseline XGBoost model achieved approximately 79.9% accuracy.

HHowever, additional metrics showed much stronger performance for the dominant rain and sun classes compared to minority classes.4. Model Comparison

The following models were compared:

* Dummy Classifier
* Random Forest
* XGBoost
* Class-weighted XGBoost

Random Forest achieved strong overall classification performance, while weighted XGBoost improved results for some minority weather categories.

This demonstrated that the highest overall accuracy does not always reflect the best performance across all classes.

5. Handling Class Imbalance

Class weighting was applied to give greater importance to less frequent weather conditions.

Models were evaluated using:

* Accuracy
* Balanced Accuracy
* Macro-F1
* Weighted-F1
* Precision
* Recall
* Confusion Matrix

6. Hyperparameter Optimisation

GridSearchCV was used to optimize XGBoost.

Instead of optimizing solely for accuracy, macro-F1 was used to ensure each weather class contributed equally to model selection.

The selected XGBoost parameters included:

* Learning rate: 0.03
* Maximum depth: 3
* Gamma: 1
* Number of estimators: 100

7. Model Interpretation

Confusion matrices identified classification errors and highlighted which weather conditions were most difficult to distinguish.

Feature importance was analyzed to determine which meteorological variables contributed most to model predictions.

---

Next-Day Weather Prediction

The project was extended from same-day classification to a genuine forecasting problem.

The next-day model was designed to use only information available before the day being predicted.

To prevent data leakage:

* Data was ordered chronologically.
* The target variable was shifted to represent the following day’s weather.
* Lagged and rolling weather features were created.
* The final 20% of observations were reserved as the test set instead of randomly sampling data.

The forecasting dataset contained 23 engineered features.

Forecasting Results

For next-day prediction:

* Random Forest: 64.0% accuracy
* Weighted XGBoost: 62.7% accuracy
* Weighted XGBoost achieved slightly higher balanced accuracy.

Both models substantially outperformed the naive baseline.

The resultsThe results also showed that genuine next-day forecasting is more challenging than classifying weather using same-day measurements.ndings

* Rain and suRain and sun were predicted more reliably due to having significantly more training examples.ses such as drizzle, fog and snow remained more difficult to classify.
* Evaluating only accuracy would have concealed weaknesses in minority-class performance.
* Class weighting improved recognition of some less frequent weather classes.
* Chronological validation provided a more realistic assessment of forecasting performance.
* Feature engineering with historical observations enabled the project to progress from classification to genuine prediction.

---

Limitations

* The dataset is relatively small and highly imbalanced, limiting model generalizability.
* Rare weather conditions have few examples.
* ThThe next-day model uses only the meteorological variables available in the dataset.ThThis project is intended as a machine learning portfolio study, not an operational weather forecasting system.

Future Improvements

Future development may include:

* Additional meteorological variables.
* Longer lag windows.
* Time-series cross-validation.
* Resampling methods for minority classes.
* Probability calibration.
* More advanced ensemble models.
* Sequence-based deep learning approaches.
