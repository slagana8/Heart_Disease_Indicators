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

I decided to oversample the positive class because the data was extremely unbalanced. After doing this it decreased the models ability to predict the negative class but greately improved its ability to predict the postive class from 9% to 79%

I then undersampled the negative class to see if this would have a greater improvement than oversampling but oversampling proved to be a stronger model. 

I used silhouette score and inertia to determine the best amount of clusters for this data set was two and applied it to my model but found it did not make any improvements. 

Since my classes are very unbalanced I decided to use SMOTE to create more of the positive class since the data consists of mostly people who don't have heart disease. After doing this, accuracy went down to 75% but it significantly increased the models ability to predict the positive class. 

## Final Decision

After running and tuning multiple models I believe the best model for production is the model done by oversampling the positive class. 

Even though the accuracy score goes down and its ability to predict the negative class weakens it gets a significant amount better at predicting the positive class from predicting 9% of true positives to predicting 79% of true positives. 

I believe this is the best model because in this case we are trying to predict if the patients have heart disease and better predicting true positives will lead to patients getting the treatment they need

![Oversampling](https://user-images.githubusercontent.com/99693002/166312917-604b374d-cad0-4faa-a63b-796a869636e0.png)

