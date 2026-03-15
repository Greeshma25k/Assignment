<h2>Student Exam Score Prediction</h2>
Problem Statement
The primary goal of this project is to predict student exam scores based on various input features. By understanding which factors most significantly influence exam performance, we aim to build a predictive model that can identify students who might need additional support or to highlight key areas of focus for academic improvement.

Dataset Description
The dataset (df_students) was synthetically generated for this analysis and contains 20 rows. Each row represents a student, and the dataset includes the following columns:

Hours_Studied: The number of hours a student studied for the exam (an integer between 1 and 9).
Previous_Scores: The student's score on a previous exam (an integer between 50 and 94).
Exam_Score: The target variable, representing the student's score on the current exam (an integer between 0 and 100), generated based on a linear combination of Hours_Studied and Previous_Scores with added random noise.
Interaction_Feature: A new feature created by multiplying Hours_Studied and Previous_Scores.
Model Used
Linear Regression models from sklearn.linear_model were used throughout this analysis. Different configurations were explored to understand feature importance and potential for overfitting:

Original Model: Linear Regression using Hours_Studied and Previous_Scores (trained on train-test split).
Single Feature Models: Linear Regression using only Hours_Studied or only Previous_Scores (trained on train-test split).
Interaction Feature Model: Linear Regression using Hours_Studied, Previous_Scores, and Interaction_Feature (trained on train-test split).
Full Dataset Models: Linear Regression using single features (Hours_Studied or Previous_Scores) trained and evaluated on the entire dataset.
Model performance was evaluated using Mean Absolute Error (MAE) and R2 Score.

Results
Below is a summary of the model performances:

Model Configuration	MAE	R2 Score
Original Model (Hours_Studied, Previous_Scores) (Train-Test Split)	1.51	0.98
Model (Hours_Studied only) (Train-Test Split)	5.21	0.80
Model (Previous_Scores only) (Train-Test Split)	5.97	0.57
Model (with Interaction Feature) (Train-Test Split)	2.02	0.97
Model (Hours_Studied only) (Full Dataset)	6.10	0.67
Model (Previous_Scores only) (Full Dataset)	7.37	0.55
Conclusion
Feature Importance:
The Original Model, utilizing both Hours_Studied and Previous_Scores, delivered the best performance with the lowest MAE (1.51) and highest R2 Score (0.98). This indicates that both features are highly significant and contribute effectively to predicting exam scores. Hours_Studied was found to be a stronger individual predictor than Previous_Scores.

Interaction Feature:
The interaction term did not significantly improve the model's predictive power over the original additive model. This suggests that for this dataset, a linear combination of Hours_Studied and Previous_Scores already captures most of the variance in exam scores.

Overfitting Analysis:
While typical overfitting checks involve comparing train-test split performance to full-dataset performance, the small size of this dataset (20 samples) introduced variability that led to unexpected results in the single-feature models (where full-dataset performance was slightly worse than test-set performance). However, the excellent performance of the Original Model on the test set (R2 = 0.98) suggests good generalization and no severe overfitting in the best configuration.

In summary, both the hours studied and previous academic performance are crucial indicators of future exam success. Their combined effect provides a highly accurate linear model for predicting student exam scores.
