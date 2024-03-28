# The-Framingham-heart-study

In this study, we aim to predict the 10-year risk of CHD (Coronary Heart Disease). CHD has been the leading cause of death worldwide since 1921, but since 1950 (after the Framingham study), age-adjusted death rates have declined by 60%. CHD is a disease of the blood vessels supplying the heart. To predict CHD, we need to evaluate risk factors that can increase the chances of the disease. These factors help us to identify important risk factors for a successful prediction of CHD.

What are Risk Factors? 
  Risk Factors are the variables that increase the chances of a disease.
  
Here we built a model in R using the Framingham data in a CSV file to predict and prevent heart disease. 
hypothesized CHD risk factors that were collected for the study, including:

- Male
- Age
- Education: some high school (1)/ high school/GED (2)/ some college/vocational school (3)/College (4)
- Current smoker (0,1), cigsPerDay
- BPmeds
- PrevalentStroke
- PrevalentHyp
- Diabetes

In the end, we want to predict 'TenYearCHD.' 

In the training set and test set, we want to calculate what percentage of the patients have CHD=1 (meaning how many patients in the training sets have already developed CHD in 10 years), and if the ratio is the same in both sets, it means that we created our training and test data set correctly.

In FraminghamTrain, we go to the Pivot tab and count variables that have been set to 1 and 0, so categorical variables = TenYearCHD. We then create a pivot table for the TrainingSet_CHD=1. We can also normalize it and get the percentage out of the numbers:  Normalizing by ---> Total --> percentage_TrainingSet_CHD=1.

In FraminghamTest-->  go to Pivot tab --> we want to count variables that have been set to 1 and 0, so categorical variables = TenYearCHD --> create pivot table -- TestSet_CHD=1

For the next step, we want to run a logistic regression model on the training dataset (because our variable is 0,1) and predict TenYearCHD with that model and evaluate the effect of sex, age, and smoking in TenYearCHD. We use Logistic Regression/Training set to do this.

Based on the Coefficient column in the model, we know that the probability of developing CHD in males is higher than in women because the number is positive(Sex). By getting older, the probability of developing CHD is also higher(Age). However, the Smoker variable is not a good risk factor to consider because it's counterintuitive and doesn't make sense, so the model has multicollinearity.

Now we want to evaluate the accuracy of our built model in our test dataset:
We go to:
    Model --> predict tab --> predict the model's prediction in the test dataset.
  so the prediction column will show us the probability of developing CHD in 10 years. We store this prediction in a column and store it in our dataset. If we go to the Data-->Test dataset, we have a pred_logit column.

For the next step:
, we create a class of probability: ---> Transform -->create a new variable: predictCHD=ifelse(pred_logit >0.5,1,0))--> class prediction

This classifies the prediction into 1 or 0. We then create a confusion matrix and calculate accuracy. In this case, the accuracy of our model in the test dataset is 85%.

