# Salary Data Analysis and Prediction

This project analyzes salary data to explore the factors associated with salary differences and to build a machine learning model for salary prediction.

The project includes data cleaning, feature engineering, exploratory data analysis (EDA), data visualization, and a Linear Regression model built with Python.

## Project Workflow

The project follows these main steps:

1. Data loading and initial exploration
2. Data cleaning and handling missing values
3. Data type conversion and categorical encoding
4. Duplicate and potential data error investigation
5. Feature engineering from job titles
6. Exploratory data analysis and visualization
7. Data preparation for machine learning
8. Linear Regression model training
9. Model evaluation using MAE and R²

## Dataset

The dataset contains salary information along with demographic, educational, and professional attributes.

The main features are:

- **Age** – Employee age
- **Gender** – Employee gender
- **Education Level** – Highest education level
- **Job Title** – Employee job title
- **Years of Experience** – Total years of professional experience
- **Salary** – Employee salary

After removing missing values, the dataset contains **373 records**.

During feature engineering, an additional feature called **Job Level** was created from the Job Title column with four categories:

- Junior Level
- Senior Level
- Management
- Other

## Data Cleaning and Feature Engineering

Several preprocessing steps were performed to prepare the dataset for analysis and modeling:

- Missing values were identified and removed.
- Numerical columns were converted to appropriate data types.
- Gender and Education Level were encoded into numerical values.
- Duplicate records were investigated. They were retained because the dataset does not contain a unique employee identifier, so identical records could represent different individuals.
- A suspicious salary value of 350 was identified. A record with the same job title and characteristics had a salary of 35,000, so the value was corrected to 35,000.
- A new `Job Level` feature was created from `Job Title` using keyword-based rules to classify positions as Junior Level, Senior Level, Management, or Other.

## Key Findings

The exploratory data analysis revealed several important patterns:

- Years of Experience showed a strong positive correlation with Salary, with a correlation coefficient of approximately **0.93**.
- Average salary differed considerably across job levels.
- Management positions had the highest average salary among the defined job-level categories.
- Senior-level positions also showed relatively high salaries compared with Junior-level positions.
- The salary distribution within the `Other` category contained several high-salary positions, including executive roles such as CEO, VP, and Chief-level positions.
- This highlighted a limitation of the simplified Job Level classification used in the project.

## Machine Learning Model

A Linear Regression model was developed to predict salary.

The model used the following features:

- Age
- Gender
- Education Level
- Years of Experience
- Job Level

The `Job Level` feature was converted into dummy variables using one-hot encoding with `drop_first=True`.

The dataset was divided into **80% training data** and **20% test data** using `random_state=42`.

## Model Performance

The model was evaluated on the test data using Mean Absolute Error (MAE) and R² score:

- **Mean Absolute Error (MAE): 10,363.62**
- **R² Score: 0.893**

The MAE indicates that the predicted salaries differed from the actual salaries by approximately **10,364** on average.

The R² score indicates that the model explained approximately **89.3% of the variation in salary** in the test data.

The Actual vs. Predicted Salary visualization showed that most predictions were relatively close to the ideal prediction line, although larger errors occurred for some high-salary positions.

## Technologies Used

- Python
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Git & GitHub

## Limitations

The `Job Level` feature was created using simple keyword-based rules based on job titles. As a result, some executive positions such as CEO, VP, and Chief-level roles were classified as `Other`.

The dataset also does not contain a unique employee identifier, which makes it difficult to determine whether identical records are true duplicates or different employees with the same characteristics.

## Future Improvements

Possible improvements to this project include:

- Creating a more detailed classification of job titles and seniority levels
- Testing additional regression models and comparing their performance
- Investigating additional feature engineering approaches
- Using a larger and more detailed salary dataset