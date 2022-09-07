
Executive Overview

Problem Statement 

Larson Texts, Inc is a company in Erie, PA that has been producing mathematics textbooks and educational material for high schools for over 45 years. The company is developing a subsidiary company, Big Ideas Learning, which will produce textbooks for elementary school students. 
The marketing department wants to use subreddits related to teaching to advertise its textbooks to teachers. We will use existing reddit data from Elementary School and High School teachers in order to train a model to categorize a block of text as coming from one group or the other. 
We can use the model to make sure that the text of the advertisement would be classified and  fit stylistically into the correct education level. 


Import the libraries 

Import comments from subreddits 
•	r/ElementaryTeachers submissions  and  r/ElementaryTeachers comments  (1,820) 
•	r/Teachers comments that include the term “elementary school” (605)
•	r/HighSchoolTeachers submissions  and r/HighSchoolTeachers comments  (200) 
•	r/Teachers comments that include the term “high school”(2,881)

Clean the data Sets 
•	Get rid of  redacted comments. 
•	Delete hyperlinks and website addresses. 
•	Get rid of duplicates.
•	Get rid of accent marks, umlauts, and other special marks. 
•	Get rid of contractions 
•	Check for spelling mistakes 
•	Strip just the words from comments (no punctuation or special symbols)
•	Remove stop words. 
•	Remove special words. 
•	Convert to word lemmas. 
•	Tag the words with parts of speech and keep the adjectives. 
	
Clean Data Set
Study Each Data Set 
•	Find the top  used words for r/ElementaryTeachers
•	Find the top  used words for r/highschoolteachers 
•	Interesting finding: 
o	Elementary School teachers use the word “teacher” 0.35 times per comment and the word “student” or “kid” 0.41 times per comment.  
o	High School teachers use the word “teacher” 0.90 times per comment, the word “student” or “kid” 1.7 times per comment.  

Model with Naïve Bayes 
Vectorization: CountVectorize
Parameter 1: max_df = 0.70
Parameter 2: 
Train Set Accuracy: 0.896
Test Set Accuracy: 0.795

Model with Logistic Regression 
Vectorization: CountVectorize
Parameter 1: max_df = 0.80
Parameter 2: model_C = 0.2575
Train Set Accuracy: 0.994
Test Set Accuracy: 0.827

Conclusion: 
The best classification model was a Logistic Regression model. 
The overall accuracy for the test data set, or the total number of comments that were correctly classified, is 83% .

For future analysis, we can: 
•	Obtain more data from subreddit r/Teachers 
•	Explore the difference between “teacher centric” and “student centric” comments.  
•	develop a model that instead of classifying a block of text as one of two categories, puts the text on a spectrum between two categories. 
