# Titanic - Machine Learning from Disaster Model Card

## Basic Information
- **Name**: Tapiwanashe Emmanuel Matare
- **Email Address**: tapiwanashe.matare@gwmail.gwu.edu
- **Date**: [4 December 2024]
- **Model Version**: 1.0
- **License**:License
MIT License


- **Model Implementation Code**: [Link to Colab](https://colab.research.google.com/drive/1hM_9FXe61U-6uMEgViwE-vmaZCpdamYh#scrollTo=qV1AOzzGyK7h) 
  
### Intended Use
- **Intended Uses**: This model is intended for predicting survival on the Titanic based on passenger characteristics.
- **Intended Users**: Data scientists, researchers, and educators interested in machine learning applications.
- **Out-of-Scope Uses**: This model should not be used for real-time decision-making in critical situations.
  
## Training Data
- **Source of Training Data**: The Titanic dataset from Kaggle.
- **Training Data Division**: The training data was divided into 70% training and 30% validation.
- **Number of Rows**:
- 
  - Training Data: [623 rows]
  - Validation Data: [134 rows]
    
- **Data Dictionary**:
  | Column Name | Modeling Role | Measurement Level | Description |
  |-------------|---------------|-------------------|-------------|
  | Pclass      | Input         | Nominal           | Passenger class (1st, 2nd, or 3rd) |
  | Sex         | Input         | Nominal           | Gender of the passenger |
  | Age         | Input         | Continuous        | Age of the passenger |
  | SibSp       | Input         | Discrete          | Number of siblings/spouses aboard |
  | Parch       | Input         | Discrete          | Number of parents/children aboard |
  | Fare        | Input         | Continuous        | Fare paid by the passenger |
  | Embarked    | Input         | Nominal           | Port of embarkation (C = Cherbourg; Q = Queenstown; S = Southampton) |
  | Survived    | Target        | Binary            | Survival status (0 = No, 1 = Yes) |



## Test Data
- **Source of Test Data**: The Titanic dataset from Kaggle.
- **Number of Rows in Test Data**: [134 rows]
- **Differences in Columns**: The test data does not include the 'Survived' column.

## Model Details
- **Input Columns**: Pclass, Sex, Age, SibSp, Parch, Fare, Embarked
- **Target Column**: Survived
- **Type of Model**: Decision Tree Classifier
- **Software Used**: Python with scikit-learn
- **Version of Software**: scikit-learn version [1.5.2]
- **Hyperparameters**:
  - Max Depth: [5]
  - Min Samples Split: [2]

## Quantitative Analysis
- **Metrics Used for Evaluation**:

 
  - Below is a summary table showing the metrics for Train, Validation, and Test datasets:

| Metric      | Train   | Validation | Test   |
|-------------|---------|------------|--------|
| AUC         | 0.895773  | 0.82433     | 0.819393 |
| Accuracy    | N/A     | N/A        | 0.768657   |
| AIR         | N/A     | N/A        | 0.768657   |

The chart below shows the model's heatmap 

![Correlation Heatmap of Titanic](Heatmap.png)
 
## Model Overview
This model is a Decision Tree Classifier trained to predict *Survival Status*:
- *Survival = 0*: No (Did not survive)
- *Survival = 1*: Yes (Survived)

The chart below illustrates the model's performance based on tree depth, showcasing the Training AUC and Validation AUC.

![Tree Depth vs. Training and Validation AUC](image.png)

---

## Performance Metrics on Test Data
- *AUC on Test Data*: 0.7687
- *Accuracy on Test Data*: 0.7687

### Confusion Matrix on Test Data
| True\Predicted   | No (Survival = 0) | Yes (Survival = 1) |
|-------------------|-------------------|--------------------|
| *No (Survival = 0)* | 69                | 18                 |
| *Yes (Survival = 1)* | 13                | 34                 |

---

## Performance Metrics by Sex
### Sex = 1 (Male)
- *Confusion Matrix*:
  | True\Predicted   | No (Survival = 0) | Yes (Survival = 1) |
  |-------------------|-------------------|--------------------|
  | *No (Survival = 0)* | 65                | 7                  |
  | *Yes (Survival = 1)* | 12                | 3                  |
- *Accuracy*: 0.7816

### Sex = 0 (Female)
- *Confusion Matrix*:
  | True\Predicted   | No (Survival = 0) | Yes (Survival = 1) |
  |-------------------|-------------------|--------------------|
  | *No (Survival = 0)* | 4                 | 11                 |
  | *Yes (Survival = 1)* | 1                 | 31                 |
- *Accuracy*: 0.7447

---

## Notes
- The model is designed to predict survival status, with *Survival = 0* representing "Did not survive" and *Survival = 1* representing "Survived."
- The overall accuracy on test data is *76.87%*, with differences in accuracy observed between males and females.
- The visualization of tree depth vs. AUC highlights potential overfitting, as seen by the divergence between training and validation AUC as tree depth increases.

---

## Recommendations
- *Further tuning* of the model might reduce overfitting.
- Consider additional stratified analysis by other variables to evaluate performance consistency across subgroups.

---
  
## Ethical Considerations
### Potential Negative Impacts
- **Math or Software Problems**:
  - The model may produce biased predictions if trained on non-representative data.
  
- **Real-world Risks**:
  - Misclassification could lead to incorrect assumptions about passenger safety.

### Potential Uncertainties
- **Math or Software Problems**:
  - Variability in model performance due to changes in input data quality.
  
- **Real-world Risks**:
  - Decisions based on model predictions could affect public perception and safety measures.

### Unexpected Results
- The model's performance may vary significantly between different demographic groups (e.g., gender, age).

