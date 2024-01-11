# The-Framingham-heart-study

In this study, we want to predict a 10-year risk of CHD(Coronary Heart Disease). 
CHD has been the leading cause of death worldwide since 1921, but since 1950( after the Framingham study), age-adjusted death rates have declined 60%.
CHD is a disease of the blood vessels supplying the heart. To predict CHD, we need to evaluate risk factors (which is our independent variable). 
These risk factors help us to identify important risk factors for having a successful prediction of CHD. 

What are Risk Factors? 
  Risk Factors are the variables that increase the chances of a disease.

I built a model in R  using the Framingham data  in a CSV file to predict and prevent heart disease.

hypothesized CHD risk factors that collected for the study:
1. male
2. age
3. education: some high school(1)/ high school/GED(2)/ some college/vocational school(3)/College(4)
4. currentSmoker (0,1),cigsPerDay
5. BPmeds
6. prevalentStroke
7. PrevalentHyp
8. diabetes
9. ....


at the end we want to predict 'TenYearCHD'


in training set and test set we want to calculate what percentage of the patients has chd=1 (means how many of patients in training sets have already developed chd in 10 years)
and if the ratio were same in both sets, it means that we created our training and test data set correctly.

in FraminghamTrain-->  go to Pivot tab --> we want to count variables that has been seted to 1 and 0, so categorical variables = TenYearCHD --> create pivot table -- TrainingSet_CHD=1
We can also normalize it  and get the percentage  out of the numbers: Normalized by --> Total --> percentage_TrainingSet_CHD=1

In FraminghamTest-->  go to Pivot tab --> we want to count variables that has been seted to 1 and 0, so categorical variables = TenYearCHD --> create pivot table -- TestSet_CHD=1

For next step, we wanna run a logistic regresion model on Training dataset (because our variable is 0,1 ) and predict TenYearCHD with that model andevaluate the effect of sex,age, smoking in TenYearCHD---> LogisticRegression/Trainingset

SEX: based on the Coefficient column in the model, for male, because the number is positive, we know that probability of vdeveloping of CHD in  males is more than  women.
AGE: By getting older, the probability of developing chd is getting higher
SMOKER: it's counter intuitive, kind of doesn't make sense so the model has multicolinearity---> so Smoker variable is not a good risk factor to considered.

Now we want to evaluate the accuracy of our buildedmodel in our test dataset:
 MOdel-->predict tab---> prediction of model in test dataset
 so the prediction column will show us the probability of the developing  chd in 10 years--> we store this prediction in a column and STORE it in our dataset.--> if we go to the Data--> Test dataset--> we haave a pred_logit column.

 next step: class of probability: -->Transform--> create new variable:predictCHD=ifelse(pred_logit >0.5,1,0)) --> class prediction

 create confusion matrix and calculateaccuracy. in this case accuracy of our model inour test data set is 85%.
