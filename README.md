# student-performance

1. Introduction
This project aims to build a predictive model for student exam scores based on various student performance factors. I used a dataset that contains various features such as study hours, attendance, previous scores, motivation level, parental involvement, and more. The goal is to predict the Exam Score based on these factors using a machine learning model.

2. Data Import and Preprocessing
2.1 Importing the Dataset
First, I imported the dataset into a jupyter notebook. The dataset contains features such as:

Hours_Studied: The number of hours the student spends studying.
Attendance: The attendance percentage of the student.
Previous_Scores: Scores obtained by the student in prior exams.
Motivation_Level: A categorical feature representing the student's motivation (e.g., High, Medium, Low).
Parental_Involvement: A categorical feature representing the involvement of parents in the student's education (e.g., High, Medium, Low).
Sleep_Hours, Tutoring_Sessions, etc.

2.2 Handling Missing Values
After loading the dataset, I checked for missing values and found that three columns had many null values:

Teacher_quality: This column was dropped due to a large number of missing values.
Parental_Education_Level and Distance_from_Home: These columns were filled with the mode of the respective columns instead of being dropped.

2.3 Ethical Considerations
I visualized the distributions of five sensitive columns, including Parental_Education_Level and Distance_from_Home. Upon analysis, I concluded that these columns might introduce bias into the model, so I decided not to include them as features in the final model to ensure fairness and ethics.

3. Exploratory Data Analysis (EDA)
3.1 Distribution and Skewness Check
I then visualized the distributions of the columns, particularly focusing on the target variable, Exam_Score. Upon examining the Exam_Score distribution, I noticed that the data was positively skewed. Since linear regression models assume normality of residuals, this skewness could affect the model's accuracy.

3.2 Transformation to Correct Skewness
To correct the positive skewness, I first applied a log transformation to the Exam_Score column. This significantly reduced the skewness but still left some room for improvement. Therefore, I applied a Box-Cox transformation, which gave me a more symmetric distribution and an even better result in terms of skewness.

4. Outlier Detection and Removal
4.1 Z-Score Method for Outlier Detection
Next, I checked for outliers using the Z-score method. This method helps to identify data points that are significantly different from the rest of the dataset. I identified and removed these outliers to ensure that they do not disproportionately affect the model's performance.

5. Model Training
5.1 Train-Test Split
I then split the cleaned data into a training set (80%) and a test set (20%) to evaluate the performance of our model on unseen data. The split ensures that we have a fair estimate of how the model would perform in real-world conditions.

5.2 Label Encoding for Categorical Feature
Since the Motivation_Level column is a categorical feature, I used Label Encoding to convert it into numerical values so it could be used in the regression model.

5.3 Model Selection
For our predictive model, I chose Linear Regression as the initial model. Linear regression is a simple and widely used model that works well for predicting continuous variables when there is a linear relationship between the features and the target variable.

6. Model Evaluation
6.1 Linear Regression Model Performance
After training the linear regression model, I evaluated it on the test set. The evaluation metrics are:

Mean Squared Error (MSE): A measure of the average squared difference between actual and predicted values. Lower values indicate better accuracy.
MSE: 2.4685
R-squared (R²): A measure of how well the model explains the variance in the target variable. It ranges from 0 to 1, where a value closer to 1 indicates better performance.
R²: 0.7610
6.2 Interpretation of Results
MSE = 2.4685: This value indicates the average squared difference between the predicted and actual exam scores. While lower values of MSE are better, this MSE suggests that the model is fairly accurate in predicting exam scores, but there might still be room for improvement.
R² = 0.7610: This value means that approximately 76.1% of the variance in exam scores is explained by the features in the model. This is a strong R² value, indicating that the model captures most of the factors influencing the exam score.
7. Conclusion
The Linear Regression model performs reasonably well with an R² of 0.7610 and an MSE of 2.4685.
The results suggest that the features used (Hours Studied, Attendance, Previous Scores, Motivation Level) have a significant relationship with the Exam_Score.
