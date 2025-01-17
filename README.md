###Child Mind Institute - Problematic Internet Use
This repository contains the solution for predicting the Severity Impairment Index (sii) of participants based on the Healthy Brain Network (HBN) dataset. The project leverages various machine learning techniques to analyze physical activity data, fitness assessments, and internet usage behavior to predict problematic internet use among children and adolescents.

###Table of Contents
Dataset Description

Data Files

HBN Instruments

Actigraphy Files and Field Descriptions

Installation

Usage

Approaches and Techniques

First Approach

Second Approach

Third Approach

Fourth Approach

Results

Reflection

Contributing

License

###Dataset Description
The Healthy Brain Network (HBN) dataset is a clinical sample of approximately five-thousand 5-22 year-olds who have undergone both clinical and research screenings. The objective of the HBN study is to find biological markers that will improve the diagnosis and treatment of mental health and learning disorders from an objective biological perspective.

The goal of this project is to predict a participant's Severity Impairment Index (sii), a measure of problematic internet use, using physical activity data and internet usage behavior data.

###Data Files
The competition data is compiled into two sources:

Parquet Files: Contain accelerometer (actigraphy) series data.

CSV Files: Contain tabular data from various clinical instruments and questionnaires.

HBN Instruments
The tabular data in train.csv and test.csv comprises measurements from a variety of instruments. These instruments include:

Demographics: Information about age and sex of participants.

Internet Use: Number of hours of computer/internet use per day.

Children's Global Assessment Scale: Numeric scale to rate the general functioning of youths.

Physical Measures: Blood pressure, heart rate, height, weight, and waist/hip measurements.

FitnessGram: Cardiovascular fitness assessments and health-related physical fitness assessments.

Bio-electric Impedance Analysis: Measures key body composition elements like BMI, fat, muscle, and water content.

Physical Activity Questionnaire: Information about children's participation in vigorous activities.

Sleep Disturbance Scale: Scale to categorize sleep disorders in children.

Actigraphy: Ecological physical activity measurement via a research-grade biotracker.

Parent-Child Internet Addiction Test (PCIAT): Measures characteristics associated with compulsive internet use.

Actigraphy Files and Field Descriptions
The actigraphy data includes:

X, Y, Z: Acceleration measures along each axis.

enmo: Euclidean Norm Minus One of all accelerometer signals.

anglez: Angle of the arm relative to the horizontal plane.

non-wear_flag: Indicates if the watch is worn.

light: Ambient light measure in lux.

battery_voltage: Battery voltage in mV.

time_of_day: Start time of a 5s sampling window.

weekday: Day of the week.

quarter: Quarter of the year.

relative_date_PCIAT: Days since the PCIAT test was administered.

###Installation
Clone the repository:

bash
git clone <repository_url>
cd <repository_directory>
Install the required libraries:

bash
pip install -r requirements.txt
Usage
Place your input data files in the same directory as main.py.

Run the script:

bash
python main.py
###Approaches and Techniques
##First Approach
Steps:

Data Loading and Preprocessing:

Loaded train.csv and test.csv, converted id to strings, and merged datasets.

Identified relevant features based on correlation with sii.

Imputation:

Simple imputation for certain columns.

KNN imputation for other metrics.

Model Training:

Used XGBClassifier with hyperparameter tuning via GridSearchCV.

Evaluated model performance using accuracy and Quadratic Weighted Kappa (QWK).

##Second Approach
Steps:

Data Visualization:

Visualized the relationship between PCIAT-PCIAT_Total and sii.

Model Training:

Used XGBRegressor with hyperparameter tuning via GridSearchCV and K-Fold Cross-Validation.

Evaluated model performance using MSE, RMSE, and R² score.

##Third Approach
Steps:

Data Preprocessing:

Performed one-hot encoding and split data into training and validation sets.

Handling Class Imbalance:

Used SMOTE to balance class distribution.

Model Training:

Used RandomForestClassifier with hyperparameter tuning via GridSearchCV.

Evaluated model performance using accuracy and QWK score.

##Fourth Approach
Steps:

Data Preprocessing:

Similar preprocessing steps with one-hot encoding and data splitting.

Handling Class Imbalance:

Again used SMOTE to handle class imbalance.

Model Training:

Used XGBClassifier with hyperparameter tuning via GridSearchCV.

Evaluated model performance using accuracy and QWK score.

###Results
First Approach:

Accuracy: 0.6077

QWK: 0.3232

Second Approach:

Best CV MSE: 315.0920

Validation RMSE: 17.7508

Validation R²: 0.2772

Third Approach:

Accuracy: 0.5803

QWK: 0.4144

Fourth Approach:

Accuracy: 0.5912

QWK: 0.3664

###Reflection
This competition was a significant learning experience, especially as the first team competition. Multiple approaches were tried, each addressing various aspects of data preprocessing, handling class imbalance, and model evaluation. Although the team didn't rank very high, the knowledge and skills gained were invaluable for future projects.
