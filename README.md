# COVID-19 Risk Factor Modeling Challenge

Responsibilities: Our team chose to split the work for this challenge based on the submission files.  The contributors are listed next to each model in the table of contents.  Although we worked on separate models, we each collaborated across the various tasks.

# Table of Contents
1. [General Remarks](#general)
2. [Covid-19 Status](#covid) -- Siqi Ke
3. [Days Hospitalized](#hostpital) -- Hena Ghonia & Khoi Mai
4. [Days in ICU](#icu) --  James Broomfield
5. [Ventilation](#ventilation) -- Chen Yu
6. [Alive or Deceased Status](#aod) -- Tianyi Sun

# General Remarks <a name="general"></a>

The general process was similar most of the models, we typically split the modelling into the following steps:
1. Preprocessing
2. Feature Creation
3. Feature Selection
4. Model Selection
5. Prediction

The following sections provide a quick overview of the process generally taken by our group.

## Preprocessing

We eliminated patients who have died before 2020 since there is no way to learn whether they will be infected or not. Then features such as marital status are label-encoded.

## Feature Creation

Features were created using binary flags for conditions, aggregation functions applied to observations, and other general feature creation techniques.

## Feature Selection

Selected based on the features based on a combination of mutual information and SHAP value. Features appear to be irrelevant are eliminated.

## Model Selection

Model selection was performed by monitoring appropriate metrics.  Randomized grid search was typically used for hyper parameter tuning.

## Prediction

There is a strong dependency between predictions in our approach to modelling.  We typically  reduced the space of patients used to train each model.  This is to account for imbalance in the data sets.  An example of this is dependency can be seen in the prediction of days in ICU.  The ICU days prediction only comes after applying the Covid-19 status model.  Some of our members chose to handle imbalances using resampling strategies, which seem to work well in their applications.

# Covid-19 Status Model <a name="covid"></a>

The features used for predicting controlled ventilation status are:

- Age of patients
- Various Conditions

## Protection and Risk Factors

Old age is the primary risk factor, that is elderly's are more likely to be identified as having COVID-19. The following table shows the feature importance for the various conditions codes:

| Feature | Importance|
|--------|------------|
|AGE     |     0.248994|
|233604007   | 0.118995|
|65710008  |   0.040994|
|162864005  |  0.029685|
|40055000  |   0.029209|
|19169002  |   0.022577|
|370143000|    0.021993|
|449868002  |  0.018703|
|15777000  |   0.017952|
|271737000 |   0.017746|

# Days Hospitalized <a name="hostpital"></a>

The features used for predicting days hospitalized are:

- Age of patients
- Various Conditions
- Various Observation values

## Protection and Risk Factors

A breakdown of feature importance and risk factors can be seen in the reports folder in our <a href="https://github.com/Ecolab-UMN-DS4C-Challenge/precisionFDA"> GitHub</a> repository

# Days in ICU Model <a name="icu"></a>

The features used for predicting duration of ICU stay are:

- Age of patients
- Various Conditions
- Various Observation values
- COVID-19 model predictions

## Protection and Risk Factors

Again, a breakdown of feature importance and risk factors can be seen in the reports folder in our <a href="https://github.com/Ecolab-UMN-DS4C-Challenge/precisionFDA"> GitHub</a> repository

# Ventilation Status Model <a name="ventilation"></a>

The features used for predicting controlled ventilation status are:

- Age of patients
- Marital Status
- Whether the patient has hypertension
- Obesity of patients
- Race of patients
- Healthcare expenses of the patient
- COVID-19 Test result of the patient
- Number of days spent in ICUs

## Protection and Risk Factors

Old age is the primary risk factor, that is elderly's are more likely to be control ventilated due to COVID. Hypertensions and obesity are also risk factors. Meanwhile having high healthcare coverage is a protection factor.

# Alive or Deceased Status <a name="aod"></a>

The features used for predicting alive or deceased status are:

- Age of patients
- Gender of patients
- Healthcare expenses of patients 
- History of pulmonary disease status of patients 
- History of Viral pharyngitis disorder status of patients 
- History of Chronic disease status of patients
- History of Cardiopathy disease status of patients 
- History of Oxygen Therapy status of patients 
- Immunization status of patients 
- COVID-19 Status prediction 
- Days Hospitalized prediction
- Days in ICU prediction
- Days ventilation prediction

## Protection and Risk Factors:

Patients who got PCV vaccine are less likely to die due to COVID-19 than those who didn't. 

Elderly's are more likely to die due to COVID-19.  

There are a fair number of COVID-19 infections died due to chronic comorbidities instead of COVID. 

COVID-19 infections are more likely to get other diseases such as heart diseases before they died. 

Patients who died due to COVID-19 are more likely to have some history disorder of pulmonary disease such as Non-small cell carcinoma of lung TNM and Primary small cell malignant neoplasm of lung TNM. 
