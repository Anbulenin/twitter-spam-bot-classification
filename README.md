# twitter-spam-bot-classification

Abstract: The popularity of twitter attracted a lot of people’s attention. Since there are many user to view the post’s many spammers have occupied a lot of space in social networks these affects the security and reputation of social network providers. Since, their major income is from advertisements if people get cheated by false advertisements created by spam bots. So, it directly affects the business of social networks providers such as twitter, facebook, linkdin etc. There are various classifiers such as Decision tree classifier, Random forest classifier, MultinominalNB classifier which are used for classifying bots vs. normal users. These classifier have managed to give the accuracy score of 86% to 92% on recent datasets retrieved from twitter API .Here we have modified these classifiers, which gave the accuracy score of 97% on identifying spam bots on twitter.

1. Introduction 
Spam’s on the internet have become a menacing presence as the Web has grown older. More so nowadays as they have occupied social networks which are the primary means of getting information for millions of people around the globe. Primarily we have targeted Twitter as many accounts with high usage volume are attacked by the spam bots. As Twitter is linked with other major social networking sites like Facebook, Instagram.It is sufficient to track spam bot on twitter. The generic algorithms for detecting spams on the internet have been developed throughout the years. The basic metrics previously used to detect spam bots have used various classifiers like decision tree, Random forest, multinomialNB. We have utilized these algorithms as well as applied our own constraints on the attributes .Values are acquired from the twitter API. This is a machine learning based approach to classify users from bots. 

2. Existing system
1. Alex Hai Wang (2011) has used Bayesian classifier in terms of F-measures which gave the accuracy score of 89%.
2.Chao Yang, Robert Chandler Harkreader, Guofei Gu(2009) have used Random Forest, Decision Tree, Decorate, Naive Bayesian classifiers and achieved the accuracy score of  88.6%.
3. Hongyu GAO,Yan Chen,Kathy Lee,Diana Palsetia,Alok Choudhary (2012) have used Decision Tree
Classifier which gave the accuracy score of 81%.
4.Ayon Chakraborty, Jyotirmoy Sundi, Som Satapathy(2009) have used Random Forest, Decision Tree, SVM, Naive Bayesian classifiers which gave the accuracy score of  89%.
5. Abdullah Talha Kabakus,Resul Kara (2017) have used Naive Bayesian, SVM classifiers which gave the accuracy score of 89.6%.


3. Proposed system
Twitter offers API for retrieving the real time attributes such as the objects on the persons account status  , network usage etc., These values are retrieved by using the keys provided by the Twitter. This Twitter API delivers the file in unformatted, unstructured texts of attributes. For these data the data frames are created with columns name as attribute names such as Friends count, Poke count, Followers count etc. These datasets from the Twitter API have non ASCIEE characters and some junk values.These dataset are encoded into”latin-1” to remove the junks. In general they were in UTF-8 encoding format and the data frames are created and stored in a csv file. Here for using the csv files in python, Pandas package is used.
We performed exploratory Data analysis on the datasets by various measures. 
3.1 Identifying Missingness and imbalance in data.
3.2 Feature engineering is done on twitter id and verified columns and the values are converted into integer    data type (int).
3.3 Feature extraction is done by various constraints on the datasets. Mined feature will Detect bot’s on datasets.
3.4 Predicting bots and unnecessary attributes are dropped to get more accuracy.

3.1 Identifying Missingness and imbalance in data
To identify the missingness in data, Heat map of training data is plotted. This heat map will show the missing values between attributes.
Attributes such as location, description, url have more missing values compared to the 
Profile picture, status, extended accounts.
Heat map of these attributes shows the missingness of attributes with each and every profile and these missingness are generalized to get appropriate results. Heatmap also show the lifetime of attributes on the datasets.
 
                                                    3.1.1Heatmap showing the missingness in data   


To identify the imbalance in data, necessary attributes are choosed which will have higher impact on classifying the datasets. Since the bots ill have more followers_count than friend_ countThis nature of bots can be used to detect them. We took two constraints to correlate the relationship between followers_list and friends_list in a dataset.
We plotted a graph between Bot friends VS Followers non bot friends VS followers
 
3.1.2 Graph between friend_count vs followers_count showing the imbalance of data


Whenever the listed count is less than 20,000 to 10,000 the probability of bots is much lesser. it also shows the imbalance of data. We plotted a graph on listed count on the twitter API datasets

 

                                       3.1.3Graph showing the imbalance of data values on listed count
3.2 Feature engineering on Datasets:

    3.2.1. Feature independence using spearman correlation:
Feature independence on datasets is obtained by using spearman’s correlation. This correlation values on various attributes have given various knowledge about the datasets. These features are used to classify the attributes.
We have taken various attributes such as id, followers_count. Listed_count, verified, default_profile etc.to find the correlation of every attributes to one another. The correlation values of datasets are plotted in a graph.

 

This graph gives two constraints on nature of twitter datasets
1. There is no correlation between id, status_count, default_profile, and default_profile image and target variables.
2. There is strong correlation between verified, listed_count, friends_count, Followers_count and target variables. With these results, screen_name, name, description. Status is used in feature engineering.















Spearman’s correlation on twitter attributes
3.2.2 Performing feature engineering
To perform feature engineering a Bag of words model is created to identify the given
Target profile is bot or not. There are bag of words model contains list of words that refers to bots
Bag of words for twitter bot:-
        bot|b0t|cannabis|tweet me|mishear|follow me|updates every|gorilla|yes_ofc|forget expos|kill|clit|bbb|butt|fuck|XXX|sex|truthe|fake|anony|free|virus|funky|RNA|kuck|jargonnerd|swag|jack|bang|bonsai|chick|prison|paper|pokem|xx|freak|ffd|dunia|clone|genie|bbbffd|onlyman|emoji|joke|troll|droop|free|every|wow|cheese|yeah|bio|magic|wizard|face
Bot|b0t|cannabis|mishear|updates every”
To check whether the target variables contains bot or not, these variables such as
 Screen name, name, description, status are converted into binary using factorizer Algorithms. Then the converted variables are checked whether it contains bot or not.

3.3 Feature extraction
Feature extraction is done by checking the binary listed counts of individual twitter accounts. If the listed count is less than >20000 we are setting the flag variable as false
i.e. they are normal users.
Another feature is extracted by the buzz feed occurrences on datasets. If the description 
Contains buzz feed then that is a bot.

3.4 Predicting bots 
With the features extracted from various constraints, datasets are trained and with the
Classifier bots are predicted
With the train and test data sets accuracy of the algorithm are measured and compared
With other algorithms
Then receiver operating characteristic (ROC) curve is plotted for this classifier model.

3.5 Architecture of spam bot detection system


 





5. Results:
For comparing the efficiency of our classifier we implemented three existing classifiers
With the same data sets and our classifier
Existing classifiers:-
 5.1 Decision tree classifier, 
5.2 Random forest classifier,
5.3 multinominalIB classifier
5.4 Our classifier

Table1: Data sets used:

Data Set	Size	Data Description
Data collection (api)	156kb	Shape(100,20)
Train data 	5mb	Shape(2796,20)
Test data	1mb	Shape(576,20)
5.1 Decision tree classifier:
This classifier on train and test datasets gave an accuracy score of 87%
Roc curve for decision tree classifier:
 
5.2 MultinomialNB classifier:
This classifier on train and test datasets gave an accuracy score of 55%
Roc curve for MultinomialNB classifier:
 

5.3Random Forest classifier:
This classifier on train and test datasets gave an accuracy score of 82%
Roc curve for Random forest classifier:
 
5.4Our classifier:
This classifier on train and test data set gave an accuracy score of 97%
Roc curve for our classifier:
 

Table 2: Accuracy score comparison of classifiers:-

Accuracy score	Tanning set	Test set
Decision tree classifier 	0.89	0.87
multinominalNB classifier	0.81	0.78
Random forest classifier	0.82	0.79
Our classifier	0.97	0.93
