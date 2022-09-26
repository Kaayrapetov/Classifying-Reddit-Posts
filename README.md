
### Introduction

A significant portion of data that exists in the world today is in the form of text that is written by humans to communicate with other humans. Since computers cannot understand human language, they cannot be used to process or analyze this text. **Natural language Processing** (NLP) is a field of linguists and computer science that uses computational tools that allow computers to analyse human language. NLP is used with machine learning classifiers to analyse human language data. This study aims to compare a handful of machine learning classifiers in thier ability to classify text data into the appropriate category. 

### Business Problem Statement 

Larson Texts, Inc is a company in Erie, PA that has been producing mathematics textbooks and educational material for high schools for over 45 years. The company is developing a subsidiary company, Big Ideas Learning, which will produce textbooks for elementary school students. 
The marketing department wants to use subreddits related to teaching to advertise its textbooks to teachers. We will use existing reddit data from Elementary School and High School teachers in order to train a model to categorize a block of text as coming from one group or the other. 
We can use the model to make sure that the text of the advertisement would be classified and  fit stylistically into the correct education level.

### Data

The data for this study was obtained from Reddit using the [Pushshift API](https://github.com/pushshift/api). The API was used to scrape the contents of posts on two subreddits: [r/ElementaryTeachers](https://www.reddit.com/r/ElementaryTeachers/) and [r/HighSchoolTeachers](https://www.reddit.com/r/HighSchoolTeachers/). These two subreddits were chosen since they are quite distinct in many ways, but also have in common the over-arching theme of education. This allowed me to use the data either as is, giving the models very distinct key-words that can be used to distingush between the two groups, or, with subreddit-specific keywords removed, making the two groups more similar. There were a total of about 24,000 subreddits scraped. Of those, about 15,500 subreddits were from High School teachers and about 8,500 subreddits were from Elementary School Teachers. 

### Models

The models I tested in this study are: 
1. **Logistic Regression Classifier** 
    which classifies an obervation based on its probability of belonging either to one class or the other.     
2. **Multinomial Naive Bayes Classifier** 
    which uses the Naive Bayes theorem to determine which class an observation belongs to  
3. **Support Vector Machine**
    which identifies the optimum decision boundary in a multi-dimensional feature space to classify observations
4. **Voting Classifier**
    which is an ensemble classifier that used an Ada Boost Classifier, a Gradient Boosting Classifier and a Logistic regression Classifier to contribute their votes for the final prediction of each observation. 

None of these models can process text data as is. Text data must first be converted in an appropriate numerical form using NLP tools that are referred to as transformers. The models were tested with two transformers, **Count Vectorizer** and **TF-IDF Vectorizer**, to find the combination that worked best.


None of these models can process text data as is. Text data must first be converted in an appropriate numerical form using NLP tools that are referred to as transformers. The models were tested with two transformers, **Count Vectorizer** and **TF-IDF Vectorizer**, to find the combination that worked best.

### Methodology

#### Data Acquisition and Cleaning
I acquired from two subreddits: [r/ElementaryTeachers](https://www.reddit.com/r/ElementaryTeachers/) and [r/HighSchoolTeachers](https://www.reddit.com/r/HighSchoolTeachers/) using [Pushshift API](https://github.com/pushshift/api). I pulled around 5000 posts from each subreddit using a custom function that used the API to scrape posts in batches of 100 going back in time. 

I then binarized the subreddit names to 0 for r/ElementaryTeachers and 1 for r/HighSchoolTeachers, and split the data into train and test sets with a test size of 30%. 

#### Gridsearching Through Model Hyperparameters
I used a pipeline and gridsearching to find the best parameters optimized for recall score for the following combinations of transformer and model:
1. Logistic regression Classifier with Count Vectorizer
2. Logistic Regression Classifier with TF-IDF Vectorizer
3. Support Vector Machine with Count Vectorizer
4. Support Vector Machine with TF-IDF Vectorizer
5. Multinomial Naive Bayes Classifier with Count Vectorizer


------------------------------
#### Results

**Model performance when trained on full dataset**
All models tested did really well in classifying posts into the corerct subreddit. SVM-Tvec (Support Vector Machine with Tfidf Vectorizer) did the best followed by Multinomial Naive Bayes, as shown in the table below. From these, I selected SVM_TVec, MNBayes and  LogReg_TVec to be tested for performance on classifying the modified dataset. 

Model|Accuracy|Recall|Precision
-----|--------|------|---------
SVM-TVec|0.988874|0.990450|0.987084
MNBayes|0.988537|0.987722|0.989071
LogReg-TVec|0.93|0.96|0.94
LogReg-CVec|0.94|0.95|0.95
SVM-CVec|0.92|0.95|0.93




#### Conclusion and Future Directions

Overall Support Vector Machine and Multinomial Naive Bayes Classifiers did the best. However Multinomial Naive Bayes had a shorter runtime and a more balanced number of false classifications between the two classes.  


 
