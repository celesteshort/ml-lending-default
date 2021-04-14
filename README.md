# Capstone Project - Lending Club Data


# Executive Summary 

 The internet has become a large part of our life.  We shop for our food, cloths and home hold items online.  Why not an unsecure loan?  

Introducing Lending Club.  Lending Club is a peer-to-peer lending company with its headquarters in San Francisco, California, began by operating as an online consumer-lending platform that allows borrowers to obtain an unsecured loan that's funded by investors.  Investors are able to search and browse the loan listings on Lending Club website and select loans that they want to invest in based on the information supplied about the borrower, amount of loan, loan grade, and loan purpose. 


 
## Problem Statements:
This is my project using Lending Tree data to predict defaults on loans using machine learning.

## Data and Data Cleaning:
We will evaluate the data from Lending Club.  This data is from 2007 to 2017.  Lending Club provided a data dictionary that contain details of all attributes of in dataset. We used that dictionary to understand more about the data columns we have and remove columns that may not impact the loan default.

While conducting EDA for this project, we found a large number of columns missing data and duplicate rows.  We removed them because most algorithm do not accept null values(NaN).

## Target Variables:
We evaluated each of the values of Loan Status feature.  We decided that our target variables - Fully Paid and Default.

![Target Variables](./images/target-variables.png "Target Variables")


## Annual Income:
The income ranged from $32 to 11m with a majority of the borrowers earning less than 175k annually. We calculated the lower and upper limits and removed all the data points beyond 161k - upper limit.  

We re-ran a histogram and noticed that it is skewed to the right.  A lot of the borrowers annual income between 40k to 75k with the median at 65k.  

![Annual Income](./images/annual_income.png "Annual Income")


## Grade and Interest Rate:
For each loan, we have two basic attributes, namely, grade and the interest rate. In Lending Club, loan grade is the letter (A-G) that is assigned to a borrower and corresponds with the interest rate that is charged for the loan.  A rate of "A" is the highest with a value of 7 and "G" the lowest with a value of 1.  The higher the expected risk of default, the higher the interest rate is set in order to offset this risk.

![Grade](./images/grade.png "Grade Rating")

The maximum interest rate was 30.9%, the lowest at 5.3% and median at 12.85%. Grade "C" had the highest default. It is a no surprise because 5% base that Lending Club adds to each loan.  

43% of Default borrowers had interest rate at 20% or greater at median income of 65_000 annually no wonder borrowers’ default.


![Interest Rate](./images/interest.png "Interest Rate")


## Employment
Employment length of 10 has the largest default rate because this group consist of those borrowers who have been employed more than 10 years.  There was no way to calculate each year after 10 because in the Employment column it is listed as 10+.

There were 8% of the borrowers with 0 years of employment.  We noticed that employment length of 0 and 1 have high default rates and wondered how can a person with 0 years employment obtain a loan?


## Confusion Matrixes for Algorithms Used:


### Logistic Regression
Logistic Regression is chosen as one of the models because it is used to predict a single outcome. Since we are trying to predict if someone will default or not, that makes this is a good algorithm for this problem.


- Accuracy training score: .9742   
- Accuracy testing score: .9739


![Logistic Regression CM](./images/cm-logistic.png "Logistic Regression Image")


### Ada Boost
We chose AdaBoost because it is a boosting algorithm that supports binary classification. It is not prone to overfit. The data has been cleaned, outliers and noise were removed.


- Accuracy training score: .9646        
- Accuracy testing score: .9642


![Ada Boost CM](./images/cm-adaboost.png "Adaboost Image")


### KNNeighbors
KNNeighbors is one of the simplest and a very popular algorithm.  It calculates the distance neighbors(data points),K. The higher the K, the better the accuracy score. 
The metric use is accuracy.  There is some overfitting, maybe because I did not balance the data prior to modeling. 


- Accuracy training score: 1.0        
- Accuracy testing score: .9784. 



![KNN CM](./images/cm-kneighbors.png "KNN CM")

### Random Forest Classifier
Random Forest does not have any assumptions like Logistic Regression. It is a forest of individual trees, trained on different subset of the train data, with its own predictions and the predictions that is the majority becomes the model's prediction - usually a high accuracy score.


- Accuracy training: .9940        
- Accuracy testing: .9818 


![Random Forest CM](./images/cm-randomforest.png "Random Forest CM")

## Conclusions 
We used four algorithms with the intention of choosing the best accuracy.  
RandomForestClassifier who successful predicted borrowers that would default on their loan because its training and testing score were and its misclassification was low.

In conclusion, the higher the interest rate, the higher chance there is default.  With the median income of 65k, issuing unsecured loans, it is easy to do so.



## Recommendations
We recommend that Lending Club re-evaluate its grade scale / interest rate because if a borrower who makes 65k is defaulting on a loan, the system is broken.  Therefore, the grading system needs to be restricted.  We suggest lowering 5% base to offset the default rate.

# References

[How to fine tune Random Forest](https://towardsdatascience.com/random-forest-hyperparameters-and-how-to-fine-tune-them-17aee785ee0d)

[Hyperparamter Tuning Random Forest](https://www.analyticsvidhya.com/blog/2020/03/beginners-guide-random-forest-hyperparameter-tuning/)

