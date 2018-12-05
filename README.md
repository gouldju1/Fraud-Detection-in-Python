# Fraud Detection in Python

For CSE 891 Data Mining at Michigan State University. Collaborated with Baylee Adams and Kyle Shope.

## Project Overview
The integrity of financial transactions is an incredibly important issue facing financial institutions and credit card companies alike. Having the ability to classify the legitimacy of a transaction to protect clients not only gives customers peace of mind, but is expensive. In 2016, according to CNBC, consumers lost more than $16B due to fraudulent transactions.

## Project Goals
Can we use historical transaction data to predict whether a transaction is fraudulent or legitimate?

## Data Overview
Our dataset from Kaggle has 594,643 rows of data, including 587,443 normal payments and 7,200 fraudulent transactions, with 10 features. The data is synthetically produced from BankSim transaction simulation software

## Data Manipulation
- Every column was a string, each with an apostrophe at the beginning and end of a cell’s content. We removed these apostrophes.
- Changed columns to the correct data type: all features categorical, except amount spent
- Removed ZIP code columns (customer and merchant), since there was only one value for each
- Utilized pandas.get_dummies to change categorical columns to binary columns

## Model Results


| Model                | Precision     | Recall   | FP    | FN    |
| :------------------: |:------------: | :------: | :--:  | :--:  |
| Naive Bayes          | 0.1957        | 0.9993   | 2     | 11695 |
| Logistic Regression  | 0.8887        | 0.7236   | 796   | 261   |
| Neural Network       | 0.8721        | 0.7624   | 684   | 322   |
| Decision Tree        | 0.9027        | 0.7212   | 803   | 224   |
| Random Forest        | 0.8845        | 0.7462   | 1096  | 421   |

We see that Naive Bayes, while it has the lowest precision, has the highest recall and lowest FP rate among the models. The Bayes model has the highest FN rate; however, this error is less serious (in a practical sense, these transactions would be flagged and fraud, and later resolved by the user, which is better than totally missing a fraudulent transaction), so we give more weight in our decision to the low FP. We also see that the neural network has a very high precision and a high recall, with the second-lowest FP score. Therefore, we rank these two models as most effective in catching fraudulent transactions.