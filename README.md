# Phase 3 Project: Terry Stop Arrest Prediction
## 1. Business Understanding
A Terry stop is a police procedure that permits law enforcement officers to briefly detain an individual based on reasonable suspicion of criminal activity. Terry Stops are controversial because they give police a wider scope of authority or freedom to make decisions which may lead to wrongful arrests. If most stops don’t lead to arrests, it raises questions about whether they are fair or effective, a concern to policy makers and civil rights organizations.

The main objective of this project is to develop a classification model that predicts whether a Terry Stop conducted by the Seattle Police Department will result in an arrest or not.
## 2. Data Understanding
The dataset to be used in this project is from [Seattle Government](https://data.seattle.gov/Public-Safety/Terry-Stops/28ny-9ts8/about_data). Each row is a unique record of a Terry stop, as reported by the officer conducting the stop.

### Columns in the dataset
1. `Subject Age Group` - Subject Age Group (10 year increments) as reported by the officer.

2. `Subject ID` - Key(Unique Identifier)

3. `GO / SC Num` - General Offense or Street Check number, relating the Terry Stop to the parent report. This field may have a one to many relationship in the data.

4. `Terry Stop ID` - Key identifying unique Terry Stop reports.

5. `Stop Resolution` - Resolution of the stop as reported by the officer.

6. `Weapon Type` - Type of weapon, if any, identified during a search or frisk of the subject. Indicates "None" if no weapons was found.

7. `Officer ID` - Key identifying unique officers in the dataset.

8. `Officer YOB` - Year of birth, as reported by the officer.

9. `Officer Gender` - Gender of the officer, as reported by the officer.

10. `Officer Race` - Race of the officer, as reported by the officer.

11. `Subject Perceived Race` - Perceived race of the subject, as reported by the officer.

12. `Subject Perceived Gender` - Perceived gender of the subject, as reported by the officer.

13. `Reported Date` - Date the report was filed in the Records Management System (RMS). Not necessarily the date the stop occurred but generally within 1 day.

14. `Reported Time` - Time the stop was reported in the Records Management System (RMS). Not the time the stop occurred but generally within 10 hours.

15. `Initial Call Type` - Initial classification of the call as assigned by 911.

16. `Final Call Type` - Final classification of the call as assigned by the primary officer closing the event.

17. `Call Type` - How the call was received by the communication center.

18. `Officer Squad` - Functional squad assignment (not budget) of the officer as reported by the Data Analytics Platform (DAP).

19. `Arrest Flag` - Indicator of whether a "physical arrest" was made, of the subject, during the Terry Stop. Does not necessarily reflect a report of an arrest in the Records Management System (RMS).

20. `Frisk Flag` - Indicator of whether a "frisk" was conducted, by the officer, of the subject, during the Terry Stop.

21. `Precinct` - Precinct of the address associated with the underlying Computer Aided Dispatch (CAD) event. Not necessarily where the Terry Stop occurred.

22. `Sector` - Sector of the address associated with the underlying Computer Aided Dispatch (CAD) event. Not necessarily where the Terry Stop occurred.
  
23. `Beat` - Beat of the address associated with the underlying Computer Aided Dispatch (CAD) event. Not necessarily where the Terry Stop occurred.

- A total of 64.8K rows and 23 columns

## 3. Data Preparation
This is where data cleaning is done. There were no duplicated, some missing values in some columns such as `Officer Squad` which were mostly filled with Unknown, outliers in `Officer Age` which were removed. There were some categories whose names were changed for better analysis and understanding, example of a column is `Weapon Type`.
Data preprocessing is also done which includes, changing categorical variables to numerical using `OneHotEncoder` and scaling of the numeric values using `MinMaxScaler`.
## 4. Data Analysis
Exploratory Data Analysis(EDA) was done after preparation. 

An example of univariate analysis:<br>

**Distribution of Officer's Age**
![Analysis 2](https://github.com/Hcton75/project-3/blob/Hcton75-patch-2/Screenshot%20(95).png)

An example of Bivariate Analysis:<br>

**Arrest Vs. Subject Perceived Race**
![Analysis 1](https://github.com/Hcton75/project-3/blob/Hcton75-patch-2/Screenshot%20(91).png)
## 5. Modelling
Data was fitted to three models, Logistic Regression model, Decision Tree model, Random Forest model. Each model had different results after evaluation. Class imbalance is addressed using SMOTE and class weights. The target variable is `Arrest Flag`.
## 6. Evaluation
Metrics used were precision, recall, f1-score, ROC curve, confusion among others. For each model, the metrics were different. 

A good example that shows difference in models used is the below image of a confusion matrix:
![Analysis 3](https://github.com/Hcton75/project-3/blob/Hcton75-patch-2/Screenshot%20(98).png)
## 7. Recommendations
Some of the recommendations include:

- **Weapon Presence is Key**: The type of weapon involved is the strongest predictor of arrest outcomes. 
   Officers should receive continued training on proper assessment and response to different weapon types.
- **Frisk Procedures**: The data shows that frisks are associated with different arrest rates. 
   Review frisk procedures to ensure they are conducted appropriately and consistently.
- **Precinct-level Analysis**: Investigate why arrest rates vary by precinct to identify best practices and ensure consistency across districts.
- **Ongoing Monitoring**: Implement regular review of these patterns to identify changes over time and address any emerging issues.
