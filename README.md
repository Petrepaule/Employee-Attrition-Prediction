# Employee Attrition Prediction

## Data Zest | Data Science Capstone Project — Cohort 7

## Project Overview

Employee attrition is a major challenge for organisations. The loss of employees increases recruitment costs, reduces productivity, disrupts team performance, and can result in the loss of valuable organisational knowledge. This project investigates employee attrition using exploratory data analysis, statistical analysis, and machine learning.

Using the IBM HR Analytics Employee Attrition dataset, we identified factors associated with employee turnover, developed classification models to predict employee attrition, evaluated their performance on unseen data, and translated the findings into practical employee retention recommendations.

This project was developed collaboratively by Data Zest as part of the TechCRUSH Data Science Capstone Project – Cohort 7.

### Team Members

- Peterpaul Chideraa Ezeazodosiaku — @Petrepaule (Team Lead)
- Juliet Oghenekevwe Ehwebayire — @julietee111
- Jeremiah Ochei Alika — @Jamalchat
- Nkwocha Eberechukwu David — @David-aloca2005
- Olaniyi Michael — @olaniyimykel
- Chiamaka Joyce Obasi  — @ChiamakaObasi
- Uchechukwu Samson Okechukwu — @Uchechukwu9
- Nkemdirim Lynda Chioma — @chiomankemdirim1-lang
- Yusuf Abdul Wasiu
- Ayomide Ali U

---

## Business Problem

The organisation wants to identify employees who may be at risk of leaving based on demographic information, job characteristics, compensation and workplace factors.

The project addresses three key questions:
1. What factors are associated with employee attrition?
2. Can machine learning accurately identify employees who may be at risk of leaving?
3. How can the resulting insights support better employee-retention strategies?

---

## Project Objectives

The project aims to:
- Understand and clean the employee dataset.
- Explore demographic, job-related and workplace factors associated with attrition.
- Identify statistically significant relationships between employee characteristics and attrition.
- Engineer and preprocess features for machine learning.
- Develop and compare multiple classification algorithms.
- Evaluate model performance using appropriate classification metrics.
- Interpret the factors contributing to model predictions.
- Develop practical, data-driven employee-retention recommendations.
- Communicate the findings through a GitHub repository, Medium article and presentation.

---

## Dataset

The project uses the **IBM HR Analytics Employee Attrition & Performance** dataset.

The dataset contains employee information covering areas such as:
- Demographics
- Job characteristics
- Compensation
- Job satisfaction
- Work environment
- Career history
- Work-life balance

### Target Variable

The target variable is `Attrition`:

| Value | Meaning |
|---|---|
| `Yes` | Employee left the organisation |
| `No` | Employee remained with the organisation |

### Data Source

IBM HR Analytics Employee Attrition Dataset — Kaggle  
[Dataset Link](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data)

*Note: The dataset is not included in this repository. Users should obtain it from the original source and place it in the appropriate local data directory before running the notebooks.*

---

# Project Methodology

The project follows a structured end-to-end Data Science workflow:

```text
Business Problem
       ↓
Data Understanding & Cleaning
       ↓
Exploratory Data Analysis
       ↓
Feature Engineering & Preprocessing
       ↓
Model Development
       ↓
Model Evaluation
       ↓
Model Interpretation
       ↓
Business Recommendations
```

### Phase 1_Data Understanding & Cleaning
The first phase focused on understanding the structure and quality of the dataset and preparing it for analysis.

**Key activities:**
- Dataset structure and dimension analysis
- Data type inspection
- Missing-value assessment
- Duplicate-value checks
- Numerical and categorical variable identification
- Identification of irrelevant or constant variables
- Data-quality checks
- Preparation of the cleaned dataset

**Outcome:** A clean and analysis-ready dataset was produced for the subsequent exploratory analysis.

### Phase 2_Exploratory Data Analysis
Exploratory Data Analysis was conducted to identify patterns and relationships associated with employee attrition.

**Analysis performed:**
- Descriptive statistics
- Attrition distribution analysis
- Numerical variable analysis
- Categorical variable analysis
- Attrition-rate comparisons
- Pairplot analysis of selected high-impact variables
- Statistical significance testing (Independent-sample t-tests, Chi-square tests, and Cramér's V analysis)

**Key Findings:**
- The analysis identified several employee, job and workplace characteristics associated with attrition.
- Factors related to overtime, career history, employee satisfaction, workplace conditions and other job characteristics showed notable relationships with employee attrition.
- These findings were subsequently used to guide the feature engineering and machine learning stages.

### Phase 3_Feature Engineering & Preprocessing
The dataset was prepared for machine learning using a leakage-aware preprocessing workflow.

**Key steps:**
- Separation of features and target
- Removal of irrelevant variables
- Train/test splitting (Stratified sampling)
- Identification of numerical and categorical features
- Encoding of categorical variables
- Scaling of numerical variables where appropriate
- Construction of the preprocessing pipeline
- Transformation of training and testing data

#### Preventing Data Leakage
A critical part of the preprocessing workflow was preventing data leakage. The dataset was split into training and testing sets before preprocessing. The preprocessing pipeline was fitted only on the training data and subsequently used to transform both the training and test datasets. This ensures that information from the unseen test set does not influence the preprocessing process.

**Final Dataset Dimensions:**
- Training features: `1,176 × 44`
- Testing features: `294 × 44`

The fitted preprocessing pipeline was saved and reused during model evaluation to ensure consistency between training and testing transformations.

### Phase 4_Model Development
Multiple classification algorithms were developed and compared using the preprocessed training dataset.

**Models evaluated:**
- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine
- Gradient Boosting
- K-Nearest Neighbours

Model performance was evaluated using metrics relevant to the business objective of identifying employees who may leave.

### Phase 5_Model Evaluation & Interpretation
The selected models were evaluated using the previously unseen test dataset.

#### Final Test-Set Performance

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|---|
| **Logistic Regression** | 75.51% | 35.63% | 65.96% | 46.27% | 0.8035 |
| **Support Vector Machine** | 81.63% | 44.44% | 59.57% | 50.91% | 0.8054 |
| **Gradient Boosting** | 85.03% | 58.82% | 21.28% | 31.25% | 0.7941 |

#### Model Selection
The Support Vector Machine (SVM) was selected as the final model based on its overall balance of performance. It achieved an 81.63% Accuracy, 44.44% Precision, 59.57% Recall, 50.91% F1-score, and 0.8054 ROC-AUC. The SVM achieved the highest F1-score and ROC-AUC among the three final evaluated models.

*Alternative Considerations:* Logistic Regression achieved higher Recall for the attrition class. This is important because a business scenario that prioritises identifying as many potential leavers as possible may prefer a model with higher Recall, even if it produces more false positives. Conversely, Gradient Boosting achieved the highest Accuracy but had substantially lower Recall for employees who actually left. Therefore, Accuracy alone was not used as the basis for selecting the final model.

#### Model Interpretation
Permutation importance was used to examine which features contributed most strongly to the predictive performance of the final Support Vector Machine.

**The most influential features included:**
- OverTime
- Number of Companies Worked
- Stock Option Level
- Years Since Last Promotion
- Distance From Home
- Hourly Rate
- Total Working Years
- Environment Satisfaction
- Work-Life Balance
- Job Satisfaction

Other influential variables included factors related to business travel, training, job role, income and relationships with managers.
---
#### Key Findings
- **OverTime** emerged as the strongest model-associated predictor by a substantial margin.
- The results indicate that attrition prediction is influenced by a combination of workload, career history, compensation-related factors, employee satisfaction, and workplace conditions.

>  **Important:** Feature importance indicates predictive association. It does not establish that a particular factor directly causes an employee to leave.

---

## Key Business Insights

The combined EDA and modelling results suggest several important areas for employee-retention strategies:

*   **Workload:** Overtime was the strongest model-associated predictor, highlighting the importance of monitoring sustained workload pressure.
*   **Career Development:** Career-related variables such as years since last promotion and overall work history were among the important predictive factors.
*   **Employee Satisfaction:** Job satisfaction, environment satisfaction, and work-life balance contributed to the predictive patterns identified by the analysis.
*   **Workplace Accessibility:** Distance from home was also among the more influential predictors, suggesting that commuting demands may be relevant to employee retention.
*   **Compensation & Recognition:** Compensation-related and employee incentive variables also contributed to the model's predictions.

---

## Business Recommendations

Based on the findings, we recommend that organisations:

1.  **Monitor and Manage Overtime:** Identify employees experiencing sustained overtime and review workload distribution, staffing levels, and work schedules.
2.  **Strengthen Career Development:** Provide clearer career progression pathways, mentoring, skills development, and internal mobility opportunities.
3.  **Review Recognition and Retention Incentives:** Evaluate employee recognition, reward, and long-term incentive programmes to support employee commitment and retention.
4.  **Improve Employee Satisfaction and Work-Life Balance:** Use regular employee feedback, pulse surveys, and manager check-ins to identify workplace issues early.
5.  **Consider Workplace Accessibility:** Where operationally feasible, consider flexible working arrangements, hybrid work, or adjusted schedules for employees facing significant commuting demands.
6.  **Develop an HR Early-Warning System:** Use predictive analytics to identify employees who may benefit from further engagement and support. *Predictions should be treated as signals for investigation rather than definitive judgements.*
7.  **Promote Responsible Use of Employee Predictions:** Protect employee privacy and ensure that model predictions are not used as the sole basis for disciplinary action, termination, promotion, or other employment decisions. The model should also be monitored regularly for performance, fairness, and potential bias.

---

## Business Impact

A data-driven employee-retention strategy can help organisations:
- Identify potential attrition risks earlier.
- Better understand employee turnover patterns.
- Target retention interventions more effectively.
- Improve employee engagement.
- Support workforce planning.
- Reduce avoidable employee turnover.

*Note: The predictive model should complement HR expertise and employee feedback rather than replace human judgement.*

---

## Limitations

The following limitations should be considered when reviewing this project:
- The dataset represents a specific organisational context and may not generalise to every organisation.
- Predictive relationships do not establish causation.
- The dataset contains historical employee information.
- Model performance may change when applied to new employee populations or organisations.
- Employee attrition is influenced by factors that may not be captured in the dataset.
- Predictions should be monitored for potential bias and fairness.

---

## Technologies Used

*   **Programming & Analysis:** Python (`Pandas`, `NumPy`)
*   **Data Visualisation:** `Matplotlib`, `Seaborn`
*   **Statistical Analysis:** `SciPy`
*   **Machine Learning:** `Scikit-learn`
*   **Development Environment:** Jupyter Notebook
*   **Version Control:** Git, GitHub

---

## Repository Structure

```text
Employee-Attrition-Prediction/
│
├── data/
│   └── README.md
│
├── images/
│   └── README.md
│
├── models/
│   └── README.md
│
├── notebooks/
│   ├── 01_Data_Understanding_and_Cleaning.ipynb
│   ├── 02_Exploratory_Data_Analysis.ipynb
│   ├── 03_Feature_Engineering_and_Preprocessing.ipynb
│   ├── 04_Model_Development.ipynb
│   ├── 05_05_Model_Evaluation_and_Interpretation.ipynb
│   └── 06_Recommendations.ipynb
│
├── reports/
│   └── README.md
│
├── .gitignore
├── README.md
└── requirements.txt
```

---

## Project Deliverables

The completed project includes:
- **GitHub Repository:** Housing code for data cleaning, EDA, feature engineering, pipeline preprocessing, model development, evaluation, and business recommendations.
- **Medium Project Report:** A comprehensive written deep-dive into the methodology and results.
- **Project Presentation:** An 8–10 slide presentation tailored for business stakeholders.

---

## Team

**Data Zest — Cohort 7**
- **Team Lead:** Peterpaul

The project was completed collaboratively by members of the Data Zest team across the different project phases.

---

## Conclusion

This project demonstrates an end-to-end application of Data Science to an employee-retention problem. Through exploratory analysis, statistical testing, and machine learning, the project identified several factors associated with employee attrition and developed predictive models capable of identifying patterns associated with employees who may leave.

Among the final evaluated models, the Support Vector Machine provided the strongest overall balance of predictive performance, achieving an F1-score of 50.91% and ROC-AUC of 0.8054 on the unseen test set. The analysis further identified `OverTime` as the strongest model-associated predictor, alongside career history, satisfaction, workplace, and compensation-related factors. 

The findings provide a foundation for proactive, data-informed employee-retention strategies while highlighting the importance of the responsible use of predictive analytics.

---
