# Predictive Maintenance using Machine Learning

Machine learning project focused on predicting industrial equipment failures using telemetry sensor data, with emphasis on operational decision-making, model interpretability, and failure detection trade-offs.

## Project Overview

This project develops a machine learning classification system to predict potential industrial machine failures using telemetry sensor data from the AI4I 2020 Predictive Maintenance dataset.

Rather than focusing exclusively on maximizing model performance, the project emphasizes the operational trade-offs between recall and precision in a highly imbalanced industrial environment, where undetected failures can lead to costly downtime and maintenance interruptions.

Several machine learning models were evaluated, including Logistic Regression, Decision Tree, Random Forest, and XGBoost. The final XGBoost model, optimized for F1-score, achieved the best balance between failure detection and false alarm reduction.

The project includes:

- Exploratory Data Analysis (EDA)
- Imbalanced classification handling
- Hyperparameter tuning
- Model interpretability
- Error analysis
- Operational insights and business limitations

One of the main findings was the significant overlap between failure and non-failure operational states, suggesting limitations of instantaneous telemetry data and potential improvements through time-series approaches.

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

## Business Problem

Unexpected industrial machine failures can generate substantial operational costs, production downtime, maintenance delays, and safety risks in manufacturing environments.

Traditional reactive maintenance strategies only respond after failures occur, often resulting in expensive repairs and operational interruptions. Predictive maintenance aims to reduce these risks by identifying potential failures before they happen using machine telemetry data.

However, predictive maintenance involves an important operational trade-off:

- False Negatives (missed failures) can result in unexpected machine breakdowns and costly downtime.
- False Positives (incorrect failure alerts) may lead to unnecessary inspections and preventive maintenance actions.

Because of this, the project focuses not only on predictive performance, but also on finding a practical operational balance between failure detection and excessive false alarms.

Additionally, the dataset presents a highly imbalanced classification problem, making metrics such as recall, precision, and F1-score especially important during model evaluation.

## Dataset

The project uses the AI4I 2020 Predictive Maintenance dataset, which contains telemetry sensor data collected from industrial machines.

Main variables include:

- Air temperature
- Process temperature
- Rotational speed
- Torque
- Tool wear

Target variable:

- Machine failure (0 = No Failure, 1 = Failure)



## Exploratory Data Analysis (EDA)

The exploratory analysis focused on understanding class imbalance, identifying relationships between telemetry variables and machine failures, and detecting operational patterns that could affect model performance.

The dataset showed a strong class imbalance, with machine failures representing only a small percentage of total observations.

As a result, traditional accuracy metrics became less informative, while recall, precision, and F1-score played a more important role throughout model evaluation.

<img width="589" height="453" alt="download" src="https://github.com/user-attachments/assets/1b05daed-3451-4579-885c-628aca48b272" />

Correlation analysis revealed moderate relationships between some telemetry variables, although no severe multicollinearity issues were detected.

Several variables appeared to contribute differently to machine behavior, suggesting the presence of non-linear relationships between telemetry signals and machine failures.

<img width="691" height="588" alt="download" src="https://github.com/user-attachments/assets/88ad4fca-af87-47ef-b59d-c6ddcdfe4598" />

Feature distribution analysis revealed significant overlap between failure and non-failure operational states.

Key observations included:

- Torque values frequently overlapped across both classes.
- Rotational speed showed broad distributions with limited linear separation.
- Tool wear exhibited similar ranges in both correctly and incorrectly classified observations.

These findings suggested that machine failures may not be easily separable using simple linear decision boundaries alone.

<img width="563" height="453" alt="download" src="https://github.com/user-attachments/assets/08c64196-dab2-4e09-a2b5-b3964a2f1bb1" />

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

The baseline Logistic Regression model achieved high recall but generated a large number of false positives, resulting in very low precision. This behavior suggested that the model was overly aggressive when identifying potential failures.

Decision Tree improved the balance between recall and precision, while Random Forest achieved very high precision at the cost of missing a larger number of actual failures.

Two optimization strategies were explored for XGBoost:

- Recall optimization prioritized maximum failure detection but introduced excessive false alarms.
- F1-score optimization produced a more balanced operational solution by maintaining strong recall while significantly improving precision.

The final XGBoost model optimized for F1-score achieved the best overall operational trade-off between failure detection and false alarm reduction.

## Final Model Selection

The final selected model was the XGBoost classifier optimized for F1-score.

Although the recall-optimized XGBoost model achieved higher failure detection rates, it also generated a large number of false positives, making the solution operationally expensive due to excessive maintenance alerts.

In contrast, the F1-optimized XGBoost model achieved a more balanced trade-off between recall and precision:

- Strong failure detection capability
- Significant reduction in false alarms
- More operationally viable performance for real-world industrial environments

The final decision prioritized operational balance rather than maximizing a single metric in isolation.

This approach reflects a more realistic predictive maintenance strategy, where both missed failures and excessive maintenance interventions generate meaningful business costs.

<img width="581" height="482" alt="download" src="https://github.com/user-attachments/assets/28c49b48-f9ae-421d-b370-edf534035d24" />

## Key Insights

- Rotational speed and torque were among the most influential predictive variables.
- Significant overlap existed between failure and non-failure operational states.
- Optimizing exclusively for recall generated excessive false positives.
- XGBoost achieved the best balance between failure detection and operational efficiency.

<img width="962" height="545" alt="download" src="https://github.com/user-attachments/assets/72c4a844-5d25-4123-a95f-c41dca61ca91" />

## Error Analysis

A detailed analysis of False Positives and False Negatives was conducted to better understand the operational limitations of the model.

One of the most important findings was that many incorrectly classified samples shared very similar telemetry patterns with correctly classified observations.

Key findings included:

- Low torque values appeared in both failure and non-failure states.
- Rotational speed distributions showed strong overlap between classes.
- Tool wear maintained similar ranges across correctly and incorrectly classified samples.

These findings suggest that some machine failures may not be fully distinguishable using isolated telemetry snapshots alone.

Additionally:

- False Positives may generate unnecessary inspections and preventive maintenance actions.
- False Negatives remain especially critical because missed failures can lead to unexpected downtime and operational losses.

Despite these limitations, the selected XGBoost model achieved a reasonable operational balance between failure detection and false alarm reduction.

The analysis also suggests that future improvements could benefit from:

- Sequential telemetry data
- Time-series approaches
- Temporal behavior modeling instead of relying exclusively on instantaneous sensor measurements

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
