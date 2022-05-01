# Heart_Disease_Indicators
Which variables have a significant effect on the increased chance of heart disease?

The data set used in this project was taken from the 2020 annual CDC survey of over 9k adults

Variables include BMI, smoking, alcohol  drinking, physical health over 30 days, mental health over 30 days, difficulty walking, sex, age, race, if their diebetic, physical activity over 30 days, general health, sleep time per day, asthma, kidney disease, and skin cancer.

Bar graph representing presence of Heart Disease

![Heart_Disease](https://user-images.githubusercontent.com/99693002/166168691-290cdecd-e32b-4bed-8aff-60cc330df070.png)



Source: "https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease"

## Data Cleaning

To prepare this data set I removed any duplicate values and confirmed there was no missing data and fixed any inconsistencies within the categorical and numerical features. This included replacing a value with a more manageable value when coding and removing a few inconsistent outliers. 

## Pre-processing

I created a function for the classification report, confusion matrix, and ROC AUC. I then used one hot encoder and scaler to prepare the data for modeling.

## Modeling 

I first ran a base model for Logistic Regression and found it had an accuracy of about 90% on the testing and training data. Despite a high accuracy score and ROC AUC it isn't stron at predicting the positive class.

I then ran a grid search to iterate through the best hyperparameters for my model. Accuracy and ROC AUC stayed the same but it got worse at predicting positive class. 

I used silhouette score and inertia to determine the best amount of clusters for this data set was two and applied it to my model but found it did not make any improvements. 

Since my classes are very unbalanced I decided to use SMOTE to create more of the positive class since the data consists of mostly people who don't have heart disease. After doing this, accuracy went down to 75% but it significantly increased the models ability to predict the positive class. 

## Final Decision
After running and tuning multiple models I believe the best model for production is the model done with SMOTE and Logistic Regression.

The accuracy went down to about 75% on the testing data but it got significantly better at predicting the postive class and declined in accuracy predicting the negative class. 

In this case, I believe it is important to have better accuracy on the positive class because that means more patients who have heart disease are being treated for it properly. 

![SMOTE](https://user-images.githubusercontent.com/99693002/166169037-832bd3a6-2e68-47a9-b497-c8adde21d5b2.png)
