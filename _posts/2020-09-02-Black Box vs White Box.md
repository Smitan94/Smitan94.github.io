---
title: "White box vs Black Box models: Importance of interpretable model in today's world"
date: 2020-09-02
tags: [Data Science, Random Forest, XG Boost, Black Box, GAM, PyGam]
excerpt: "In today's world, more and more focus is on ensuring how black box models can be interpreted and if they are really required"
---
### INTRODUCTION:

Machine Learning has come a long way in the last decade or so. With new and rapid breakthroughs in the field of computer vision and natural language processing, companies are constantly trying to play catch up with the new technologies and methodologies. A quick look at some of the best performing models on Kaggle competitions will reveal the supremacy of models such as XG Boost and Neural networks, however, when it comes to making real world decisions, companies often do not trust them. This is not only because the working of these models is often complicated to explain to a layman "business" person, it is also because, we as data scientists cannot explain the exact working of these models. This leads to a level of mistrust being placed on these models. 
So, is the alternative is to keep using models which give lower accuracy? Absolutely not! 
Many researchers have shown that there is no significant difference in the performance of machine learning models, if tuned properly, on most of the "structured" data science problems. Unstructured problem statements such as image classification and text analysis are heavily dependent on the sequence of data (either on words or on pixels) and hence feature extraction becomes a key part of the process (which is not true for our structured problem statements). In this project, we have tried to emulate the accuracy achieved by some of the more sophisticated models with simpler models.



### PROBLEM STATEMENT:

Our client asked us to create a model which will be able to identify the people who are more likely to default on their credit card loans next month. The dataset provided to us contains both their historical payments trend, balance amount and how many times have they defaulted in the last 6 months along with their demographic details.
Sneak peek at the data: A quick look at the data gave us some interesting insights-
* Women tend to default less than men as per the dataset
* Young people (age between 21 and 25) and elder people (age greater than 55) tend to default more than any other age group
* People with only "High School" as the highest level of education seem to default more


### APPROACH:

Keeping the ultimate business objective in mind and having looked at the trends present in the data, we finally decided to follow the below mentioned approach:

1. Create a model that can not only correctly identify the people who are about to default next month but also ensure that the model is not biased against a particular demographic segment. 
		The above point became a very critical part of this project since we did not want our model to rely heavily on the demographics feature of the population. The demographics feature can mislead a model since we are only working on a sample of the dataset and cannot be sure of the methodology behind the sampling of the dataset. Also, in real world, it is sometimes not possible to ignore one major segment of the population and hence we wanted our model to focus more on the payment history than on demographic attributes

2. Compare the performance of black model vs white box models



### METHODOLOGY:

To ensure we meet our business objectives, we undertook multiple steps that include:

1. Feature engineering: It was imperative to create new features from the existing columns in the dataset as doing so enables us to derive more information from the dataset and find hidden relationships between variables

	1.1 Cumulative points based on the number of times they have already defaulted. People who have defaulted multiple times are given a negative score while people who have always paid the credit on time have a positive score.

	1.2 Average payment made to the bank over the last 6 months compared against the latest amount of loan taken from bank. For e.g. if a person has been paying $500 on an average to the bank but in the current month, has taken a loan of $10,000, then it's highly likely that this person will default in the next month.

	1.3 Removal of records when there was no clear indication of why people have been marked as "defaulter" despite their records showing that they have made due payments for the last 6 months. Albeit subtle, this step prevents the model from learning from cases wherein the default status is not dependent on the payment trend but rather focuses on other features present in the dataset.

2. Working with imbalanced data: The number of people defaulting on their credit card loans is as small as 1% of the entire dataset. To enable our model to learn equally from both the classes, defaulters and non-defaulters, it was important to increase the defaulters group with synthetic data. This would prevent the model from being biased towards the non-defaulters group

### RESULT:

The class imbalance in the dataset makes identification of defaulters challenging. The associated cost of not identifying a defaulter far outweighs the cost of misjudging a person to be a defaulter. This is where metrics such as recall and precision become important.

	Recall = # of people classified as defaulters / # of people who actually defaulted

	Precision = # of people correctly classified as defaulters / # of people classified as defaulters

There is usually a trade-off between precision and recall. Higher recall leads to lower precision and vice-versa. You can read more about precision-recall trade off [here](https://towardsdatascience.com/beyond-accuracy-precision-and-recall-3da06bea9f6c).
Here is a comparison of model performance in terms of recall and precision across our four models for all the people defaulting on their credit card. This is important since the number of people defaulting is very low in our dataset.

| Model                            | Type            | Precision (for default cases) | Recall (for default cases) |
|----------------------------------|-----------------|-------------------------------|----------------------------|
| Random Forest                    | Black Box Model | 85%                           | 64%                        |
| XG Boost                         | Black Box Model | 90%                           | 76%                        |
| Logistic Regression              | White Box Model | 73%                           | 66%                        |
| General Additive Modelling (GAM) | White Box Model | 92%                           | 80%                        |



Unsurprisingly and as stated earlier, XG Boost is the better performer between the two black box models.

The white box model Logistic Regression is not a strong performer. This is because some of the features present in the dataset do not show linearity, an issue that is often faced in real world datasets, and hence logistic regression is unable to generalise a good model.

General Additive Modelling (GAM) overcomes the limitations of Logistic Regression. GAM is a powerful and yet a simple technique that combines the predictive power of black box model with the interpretability of logistic regression. It is able to achieve this because the relationships between variables are not assumed to be linear. Each feature is independently plotted against our target (can be either linear or non-linear) and is then summed up.

The main advantages of GAM are as follows:
1. Easy to interpret
2. Flexible predictor functions can uncover hidden patterns in the data
3. Regularisation of predictor functions helps avoid overfitting

You can also read this article [here] (https://multithreaded.stitchfix.com/blog/2015/07/30/gam/) which explains in a very simple way what GAM is about!

