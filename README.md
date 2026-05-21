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

<img width="737" height="565" alt="image" src="https://github.com/user-attachments/assets/85ed1330-fe34-4918-9547-9eeb595be656" />

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
| Logistic Regression | 0.80 | 0.13 | 0.23 |
| Decision Tree | 0.61 | 0.68 | 0.64 |
| Random Forest | 0.43 | 0.91 | 0.58 |
| XGBoost (Recall optimized) | 0.95 | 0.23 | 0.37|
| XGBoost (F1 optimized) | 0.76 | 0.70 | 0.73 |

<img width="1089" height="690" alt="download" src="https://github.com/user-attachments/assets/cd8be71d-77bb-4fc3-aa60-a0602774d63b" />

The initial Logistic Regression baeline achieved high recall but generated an excessive number of false positives, resulting in very low precision. This behavior suggested that the model was overly aggressive when identifying potential failures.

Decision Tree improved the balance between recall and precision considerably, while Random Forest achieved very hich precision at the cost of missing a larger number of true failures.

Two tunning strategies were explored for XGBoost:
- Recall optimization prioritized maximum failure detection but introduced excessive false alarms.
- F1-score optimization produced a more balanced operational solution by maintaning strong recall while significantly improving precision.

The final XGBoost model oprimized for f2-score achieved the best operational trade-off between detecting failures and minimizing unnecesary maintenance interventions.

## Final Model Selection

The final selected model was the XGBoost classifier optimized for F1-score

Although the recall-optimized XGBoost model achieved higher failure detection rates, it also generated a very large number of false positives, making the solution operationally expensive due to excessive unnecessaary maintenance alerts.

On the other hande, the F1-optimized XGBoost model achieved a more balanced trade-off between recall and precision:
- It maintained strong failure detection capability.
- It significantly reduced false alarms compared to the recall-focused approach.
- It provided a more operationally viable solution for real-word industrial environments.

The final decision prioritized operational balance rather than maximizing a single metric in isolation.

This approach reflects a more realistic predictive maintenance strategy, where both missed failures and excessive maintenance interventions generate important business costs.

<img width="1089" height="690" alt="download" src="https://github.com/user-attachments/assets/4b4d0be7-5caa-4d68-98c1-70395c46507b" />

## Key Insights

- Rotational speed and torque were among the most influential variables.
- Significant overlao existed between failure and non-failure operational states.
- Optimizing exclusively for recall generated excessive false positives.
- XGBoost achieve the best operational balance for the problem

<img width="1089" height="690" alt="download" src="https://github.com/user-attachments/assets/44ea2a7a-9534-4d3c-a2f3-946562d406cf" />

## Error Analysis 

A detailed analysis of False Positives and False NEgatives was performed to better understand the operational limitations of the model.

One of the most important findings was that many incorrectly classified samples shared very similar telemetry patterns with correctly classified observations. In particular:
- Low torque values frequently appeared in both failure and non-failure states.
- Rotational speed distributions showed strong overlap between classes.
- Tool wear maintained similar ranges across several correctly and incorrectly classified samples.

These findings suggest that some machine failures may not be fully distinguisbhable using isolated telemetry snapshots alone.

Additionally:
- False Positives may generate unnecessary inspections or preventive maintenance actions.
- False Negatives remain specially critical because indetected failures can lead to unexpected downtime and operational costs.

Despite these limitations, the selected XGBoost model achieved a reasonable operational balance between failure detection and false alarm reduction.

The analysis aldo suggests that future improvements could benefit from:
- Sequential telemetry data
- Time-series approaches
- Temporal behaivor modeling rather than relying exclusively on instantaneous sensor measurements.

## Limitations 

The project uses instantaneous telemetry snapshots rather than sequential temporal data. Some failure patterns may require time-series or sequential modeling approaches to improve predictive capability.

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-Learn
- XGBoost
- Matplotlib
- Seaborn
- Jupyter Notebook
