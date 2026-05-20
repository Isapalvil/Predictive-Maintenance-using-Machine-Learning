# Predictive-Maintenance-using-Machine-Learning
Machine learning project focused on predictive maintenance and industrial failure detection using telemetry sensor data, emphasizing operational trade-offs, model interpretability, and error analysis.

## Project overview
This project focuses on developing a machine learning classification system capable of detecting potential industrial mechine faiulres using telemetry sensor data from the AI4I 2020 Predictive Maintenance dataset.

The project goes beyond simply maximizing model performance by emphasizing operational trade-pffs between recall and precision in a highly imbalanced industrial setting, where undetected failures may generate significant maintenance and downtime costs.

Several machine learning models were wvaluated, including Logistic Regression, Decision Tree, Random Forest and XGBoost classifier optimized for F1-score, providing the best operational balance between failure detection and false alarms.

In addition to model development, the project includes:
- Exploratory Data Analysis (EDA)
- Imabalanced classification handling
- Hyperparameter tuning
- Model interpretability
- Error analysis
- Operational insights and limitation discussion

One of the key findings of the project was the existence of significante overlap between failure and non-failure operational states, suggesting limitations of innstantaneous telemetry data and potential future improvements through time-series approaches.

## Business Problem
Unexpected industrial machine failures can generate significant operational costs, production downtime, maintenance delays, and safety risks in manufacturing environments.


Traditional corrective maintenance strategies react only after a failure occurs, which may lead to expensive repairs and interruptions in production processes. Predictive maintenance aims to reduce these risks by identifying potential failures before they happen using machine telemetry data.

However, this problem presents an important operational trade-off. In this context:

- False Negatives (undetected failures) are highly expensive because they may result in unexpected machine breakdowns and operational downtime.
- False positives (incorrect failure alerts) also generate costs through unnecesary inspections or preventive.

Because of this, the project focuses not only on maximizing predective performance, but on finding an operational viable valance between failure detection and excessive false alarms.

The dataset also presents a highly imbalanced classification problem, making evaluation metrics such as recall, precision, F1-score especially important during model selection.

## Dataset

The project uses the AI$I 2020 Predective Maintenance Dataset, which contains telemetry sensro data collected from industrial machines.

Main variables include:
- Air temperature
- Process temperature
- Rotational speed
- Torque
- Tool wear

The dataset presents a highly imbalanced classification problem, making evaluation metrics and operational trade-offs specially important.

## Workflow

1. Business understanding
2. Exploratory Data Analysis (EDA)
3. Data preprocessing
4. Imbalance classification handling
5. Baseline modeling
6. Model comparison
7. Hyperparameter tuning
8. Error analysis
9. Model interpretability
10. Final conclusion

## Models Evaluated

- Logistic Regression
- Decision Tree
- Random Forest
- XGBoost

## Model Comparison

| Model | Recall | Precision | F1-Score |
|---|---|---|---|
