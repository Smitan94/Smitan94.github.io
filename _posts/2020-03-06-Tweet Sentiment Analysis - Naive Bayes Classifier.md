---
title: "Tweet Sentiment Analysis - Naive Bayes Classifier"
date: 2020-03-06
tags: [NLP, Sentiment Analysis, Classification, Naive Bayes]
excerpt: "To classify the sentiments behind a large corpus of tweets"
---
Today a large amount of data present around us is in the unstructured format such as bills, receipts, articles, blogs, etc. If we are to truly realize the potential of machine learning and data together then it is quintessential to be able to extract this information from these formats.

Background: Sentiment Analysis, a.k.a opinion mining, is the process of extracting subjective information that underlies a text using text analysis and natural language proecessing methods. This can be either an opinion, a judgment, or a feeling about a particular topic or subject. The most common type of sentiment analysis consists of classifying a statement as ‘positive’, ‘negative’ or ‘neutral’.

Recently, it has become a large part of companies to analyze this data and understand the reputation of their brand. This provides the companies with a more quantifiable way to get feedback on their products and any relevant associations. This form of feedbck earlier used to be both time consuming and resource intensive and hence a lot of companies are now investing significantly on managing their social media accounts along with a social media mining team.

Problem Statement: We are provided with a large corpus with a semi cleaned twitter dataset which consists of ~ 30K tweets. Our main objective is to classify these tweets into positive, negative or neutral and check the accuracy of our model


[Link to the project code](https://github.com/Smitan94/Data-Science/blob/master/Tweet%20Sentiment%20Analysis.ipynb)

Key Learnings - 

The most important step in sentiment analysis is the way you pre process or clean the data. In this analysis, pre-processing was an interative process in which after cleaning the data for the first time, I was validating my model against a validation dataset, performing an error analysis (verifying manually which tweets are mislablled) and then cleaning the data accordingly. After doing these steps couple of times, I finally stopped having performed the below mentioned steps -

| Steps taken                                                                     | Reason                                                                                                                  |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| Removing all links from the tweets                                              | We do not get any information regarding sentiments from the links themselves                                            |
| Removing all sentences with less than 3 words                                   | Not enough words to gain any useful information                                                                         |
| Converting all the words to lowercase                                           | This is to ensure we have standardised words across tweets                                                              |
| Stopwords and punctuations have been removed                                    | Not enough information from these words                                                                                 |
| Lemmatized the words                                                            | This is to ensure we do not have multiple forms of the same word                                                        |
| Removing special characters ("@","$",etc.) from the text                        | Do not get information about sentiment from these characters                                                            |
| Removing numbers from the tweets                                                | Do not get information about sentiment from these characters                                                            |
| Removing repetitive characters from the tweet (e.g. goooaaalll changed to goal) | We gain the same information from both the words and minimises the total number of word features present in our dataset |

Key Insight -

As part of the exploratory data analysis, I had posted the frequency of the top 20 words for the tweets that have been classified as positive, negative, and neutral. We notice that a lot of the top words present in the neutral list such as "good", "but", "day","work" are present in all three types of tweets. Since in these cases, adverbs and adjectives would be the ones making the difference in the tweet. For example, "beautifful day", "day sucks", and "Leave during day time" would classify as "positive", "negative" and "neutral" respectively. This will act as a major drawback to our model.

Limitations -

Since we are using Naive Bayes Classifier, the sequence of the words are not taken into consideration while classifying the tweets. This is a crucial step since tweets have to be at most 140 words and a lot of words will be overlapping amongst all three labels. We will be taking this into consideration for our next model.

