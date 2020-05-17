# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & Classification

Geoffrey Liu
General Assembly Singapore
Data Science Immersive 14

## Problem Statement

The project intends to start building a prototype classification model that can assist Reddit to predict which subreddit a post belongs to by using the titles and self text(posts) combined. The aim is to see if the model can potentially speed up the process efficiency for Reddit in detecting if posts in the subreddit should be there or moved elsewhere. Hopefully, the model can eventually be used more broadly for classification to the rest of the subreddits in the future.


## Executive Summary
The two subreddits chosen for the classfication model are

[`Personal finance`](https://www.reddit.com/r/personalfinance)
[`Student loans`](https://www.reddit.com/r/StudentLoans)

Personal finance discusses topics on budgeting, saving, getting out of debt, credit cards, investing, and retirement planning while student loans discusses on the student loan debts of individuals and financing issues related to it.
Both these posts are finance and money related and have overlapping terms and is understandably so when you consider the topics. This provides a challenge for the prototype model. 

### Scraping from Reddit

We begin the process by scraping the data which comes from Reddit's API. The data comes in a json format and it will be used to train and test the models later on. After scraping the subreddit posts they are put inside data frames and the columns retained were the name, subreddit, title and selftext. The data frames are then saved to csv format. 

### Cleaning and EDA

The csv files are read into data frames and each subreddit data frame is checked for null values and duplicates and those rows are subsequently dropped. Personal finance data frame is left with 993 rows and student loans is left with 946 rows. Both subreddit data frames are concatenated into a combined data frame and the value counts normalization for the subreddit shows: personalfinance    0.51212
StudentLoans       0.48788
It is about 0.03 difference between the proportions which is acceptable. The contents in titles and selftext columns are combined into a new column called all_text. There is a cleaning function that containing regex expression, stopwords and lemmatizing that takes out uneccessary words. I created barcharts of most freqeuntly appearing words for each subreddit and word clouds as well and checked to see if there were more uneccessary words or characters that can be added to the cleaning function to be taken out. There are common words that appear in both subreddit posts like 'loan', 'pay', and 'money'. Not surprising as both subreddits revolve around those topics. After this is done, the file is saved.

### Modeling

As a baseline accuracy, the majority class personal finance with proportion 0.51212 will be class 1 and student loans with proportion 0.48788 will be class 0. We will be doing four models process.
-GridsearchCV logistic regression count vectorizer
-GridsearchCV logistic regression TFIDF vectorizer
-Gridsearch CV multinomial bayes count vectorizer
-Gridsearch CV multinomial bayes TFIDF vectorizer

I will be using pipeline to make the transforming and estimator process easier and will be using different combinations of parameters for the gridsearchCV to find the best score. I'll select the model with the best score and will evaluate the accuracy  metric to see how the model correctly classified the class 1's and 0's over the whole data. This should be a reliable metrics as the dataset between the 2 subreddits is fairly symmetric and classifying the posts wrongly to a subreddit doesn't have a significant impact to the problem we are addressing. 

### Conlusion

|Model|Train Score|Test Score|
|---|---|---|
|GridsearchCV logistic regression count vectorizer|1.0|0.9031|
|GridsearchCV logistic regression TFIDF vectorizer|0.9656|0.9134|
|Gridsearch CV multinomial bayes count vectorizer|0.9594|0.9216|
|Gridsearch CV multinomial bayes TFIDF vectorizer|0.9718|0.9278|

The model that I have chosen is Gridsearch CV multinomial bayes TFIDF vectorizer as it has presented the best test score at 0.92 and Niave Bayes modeling is also able to work well with smaller datasets as such in this case where there's 900 plus data points for each subreddit. Also, because the data is not numerical but categorical, Naive Bayes also works well with it. I tried experimenting around with the proba treshold for the confusion matrix but still found the best treshold to be 0.5. Accuracy is a good score indicating most predicted values were properly classified to each subreddit. One thing to note is that false negative is higher than false positive and usually false negatives are seen as more severe than false positives but because our prototype model is trying to detect where posts came from two fairly similar subreddits the false negatives would be considered so severe as compared to lets say a classification where class 1 is having breast cancer and class 0 is not having breast cancer.
   
    
### The limitations and what could be recommended

As the dataset contained about 900 plus posts per subreddit, it may not be representative of each subreddit. More webscraping could be done in the future.

It is possible people's comments could be a good feature to analyze but I am not sure

Due to time restrictions I was not able to repeatedly see words that could be taken out but it could be beneficial to take out words that have similar meaning or synonymous with other words and possibly words that did not get lemmatized.

I should try more models next time like an ensemble model like random forest (Laptop started overheating and process took too long to complete)

Coefficients could help give companies intending to advertise their products and services by showing what people specifically talk about in each subreddit



 








