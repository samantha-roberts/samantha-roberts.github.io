---
title: "Text Analysis of Amazon Reviews for Prediction"
layout: splash
date: 2019-12-17
tags:
  - Sentiment Analysis
  - Tokenizing
  - NLP
  - Supervised 
  - Unsupervised
<!-- header:
  overlay_image: /assets/images/workflow_amazon.PNG -->
---
<h2><center><strong>Predicting Amazon Reviews through Text Analysis</strong></center></h2>
<p>
 <center><img src="/images/amazon.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center><br>
  
<h3><center>Description:</center></h3>
<p>
The analysis and visuals were created to study the relationship between the rating of amazon products and the words used in the review descriptions left on the products. The rating for each product is a number, having values 1, 2, 3, 4, and 5, with 5 being the highest rating. The review descriptions can be anywhere from a single word, to a short paragraph reviewing the product. The object of this analysis is to create numerical classifications using sentiment analysis to understand the efficacy of the polarity scores of text mining in classifying reviews. 
</p>
 
<!-- <ul> -->
<!-- <li> </li> -->

<p>
<em>To view the code used in this excercise please click <a href="https://jwr1015.github.io/links/amazon_reviews_analysis.html">here</a></em>
</p>

<h3><center><strong>Part 1: Document Term Matrices (DTM)</strong></center></h3>
<p>
  <center><img src="/images/dtmdf.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.1 - Document Term Matrix using Count Vectorizer</figcaption><br>
  <center><img src="/images/dtm2.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.2 - Document Term Matrix using TFIDF</figcaption><br>
  To begin the analysis process, a random sample of 10,000 was taken from the entrie dataset of Amazon reviews. This sample included the three columns in the original dataset, Rating, Title and Description. In order to create document term matrices, all words in the sample dataframe  (amazon_sample) were converted to having only lower case letters. Next, all words in the Title and Description columns were tokenized. Tokenization is the process of breaking up a sequence of strings into smaller pieces; in this case each string was broken down into tokens of each individual word in the columns. By doing this, it is easier to decide which words are linked to each rating, based off reviews of products. Next, each token in the dataframe was stemmed. Stemming is when each word (the tokens) are reduced to their stem or root form. For example, the stemmed version of the word “running” would be “run.” The stemming method used was Porter Stemmer, which is the default algorithm in Python for stemming. By definition, Porter Stemming is “the process for removing the commoner morphological and inflexional endings from words in English .” Finally, to prepare the columns for the DTMs, stop words were removed from both Title and Description columns. Stop words are commonly used words that have little to no importance. By removing stop words, it becomes easier to focus on the important words instead. The stop words removed from the dataframe were all English stop words.
</p>
<p>
	The first DTM method used was Count Vectorizer. Count Vectorizer is when each token (words, in this case) is counted and documented in a matrix. For example, if the word “run” appears 8 times in the document, then an 8 would occur in the matrix in the respective spot for “run.” This process is repeated for each token in both columns, Title and Description, for Amazon reviews. The number of terms in the matrix for this analysis was limited to 5000, with each term consisting of only one word, instead of having terms that could be a combination of multiple words. The second DTM method used was tf-idf. Tf-idf stands for term frequency- inverse document frequency. This method reflects the importance of a word/token to a document, which in this case is each Amazon review. The weights in tf-idf are used to evaluate the importance of the words in the reviews.

</p>
<center><h3><strong>Part 2: Polarity Scores and Sentiment Analysis</strong></h3></center>
<br>
<p>
  <center><img src="/images/textblob_hist.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.3 -Distribution of TextBlob Polarity Scores</figcaption><br>
  <center><img src="/images/tot_polarity_table.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.4 - Sample of Data Table with Reviews and Polarity Scores</figcaption><br>
  After each document term matrix was created, polarity scores were calculated from them. The first method to discover the polarity scores was TextBlob. TextBlob returns both a polarity score and a subjectivity score, where polarity is between -1 and 1, where -1 is a very negative word and 1 is a very positive word, and subjectivity is between 0 and 1, with 0 being very objective and 0 being very subjective. TextBlob was applied to the “cleaned” Description column (tokenized, stop-word free, stemmed) in order to have unbiased results. By plotting the TextBlob results for Description it is easy to see that the majority of words have a polarity score of 0, meaning they are not negative or positive. There is a large spike at polarity score of 0, indicating there are a lot of neutral words. However, the center of the histogram is situated slightly to the right of 0, suggesting that there are more positively polarized scores than negative. The second method used was VADER. VADER is used for both polarity (how positive or negative a word is) and the intensity of the emotion the word conveys. VADER returns positive, negative, neutral and compound scores. The compound score is the metric that’s calculated from the sum of all the ratings. Positive, negative and neutral scores are then based off the compound score, with positive seniments having a compound score greater than or equal to 0.05, negative sentiments having a compound score less than or equal to -0.05, and a neutral sentiment having compound scores less than 0.05, but greater than -0.05. The polarity and subjectivity scores for TextBlob are stored in the columns Description_Sent_pol and Description_Sent_sub, respectively. For VADER, positive scores are in the column pos, negative scores are in the column neg, neutral scores are in the column neu, and compound scores are in the column compound. 
</p><br>

<center><h3><strong>Part 3: Dimension Reduction:</strong></h3></center>
<p>
  <center><img src="/images/umap.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.5 - UMAP</figcaption><br>
  To reduce dimensionality for the Document Term Matrices, three methods were used: Sparse Principal Component Analysis (PCA), UMAP, and Locally Linear Embedding (LLE). Sparse PCA was chosen because it takes the minimum, most efficient input variables, and generally makes for a better classification method. There were twenty components chosen for Sparse PCA. The second dimension reduction technique, UMAP, is used to take the multi-dimensional space and reduce it down to 2-dimensions. By plotting UMAP it is easy to see the distribution of the product ratings with the density of UMAP. Both UMAP plots show that there does not appear to be a strategic categorization of ratings in the reduced dimensions. This is seen easily because there is not a gradual transition between colors within the plot, indicating that there is a not a separation of ratings. The third method for dimension reduction used was Locally Linear Embedding, which preserves the distances between neighbors on a local level, instead of on a global level like Principal Components do. Based off the values of the LLE columns, similar results to UMAP were obtained, where there is not any way to decipher which rating is in which LLE dimension. 
</p>

<center><h3><strong>Part 4: Clustering</strong></h3></center>
<p>
  <center><img src="/images/kmeans.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.6 - K-Means Clustering Distributions</figcaption><br>
  Three clustering techniques were attempted for this analysis: Kmeans clustering, DBScan, and Agglomerative clustering. For Kmeans clustering on both dimension reduced Document Term Matrices, seven clusters were used, with the max iteration value set to 300. DBScan had 4 clusters with a minimum amount of samples equal to 2, and Agglomerative clustering also had 4 clusters. All three clustering techniques failed to show how the dimension reduced DTMs were clustered. All plots for all clusters from these methods were normally distributed, with the majority (and the center) of the distributionsbeing located at 0. This means that there was not a difference between a review that had a rating of 1 or a review with a rating of 5, based off the polarity of the words used. This does not seem to be accurate because it would be expected that reviews with a rating of 1 would have polarity scores that are deemed negative (less than -0.05) and that reviews with a rating of 5 would have polarity scores that are considered positive (greater than 0.05), with neutral scores falling in between. 
</p><br>

<center><h3><strong>Part 5: Modeling</strong></h3></center>
<p>
  <center><img src="/images/model_comparison.png" style="margin:0 20px 20px 0;" width="800" height="800" align="middle"></center>
  <figcaption>Fig.7 - Model Comparison</figcaption><br>
  Before fitting models for the dataframes, the data was first split into training and test sets, with 80% being training data and 20% being testing data. Two supervised learning models, k-Nearest-Neighbors (KNN) and Random Forest Classifier (RFC) were run on both training sets. A variety of neighbors was executed for KNN, with values of 5, 7, 9, 11, 13 and 15. For the first KNN model run (on the TextBlob dimension reduced dataframe) the maximum accuracy score was when the model was fit with 13 neighbors and the accuracy score was 29.9%. The second KNN model run (on the VADER dimension reduced dataframe) had a maximum accuracy score of 31.85%, with the number of neighbors being 13 as well. The best Random Forest Classifier model for the first dataframe had an accuracy score of 38.3% ad for this model the number of estimators used was 500, having a minimum sample split of 5 and minimum sample leaf value of 5. The second dataframe’s best RFC accuracy score was 37.75% with the same parameters as the first dataframe’s Random Forest Classifier model.
</p>
<p>
  The two unsupervised learning models used were Gradient Boosting and XGBoost. For Gradient Boosting the best model for the first dataframe (the TextBlob dimension reduced dataframe) had an accuracy score of 36.05%, with a learning rate of 0.001, number of estimators equal to 500 and a subsample equal to 1. For the second dataframe (VADER dimension reduced dataframe) the best accuracy score had the same inputs as the first dataframe and the score was 35%. For XGBoost, out of the 55 models ran on the first dataframe, the best model had an accuracy score of 39.45%, with a learning rate of 0.1, max depth of 5, the number of estimators being 100 and the subsample being 0.8. The second model had the best accuracy score, out of 55 models, equal to 39.2%, where the feature settings were a learning rate of 0.1, maximum depth of 7, 100 estimators and a subsample of size 0.6. Overall, the best model(s) for the data were XGBoost models, with accuracy scores of 39.45% and 39.2%, for the first and second DTMs, respectively. 
</p><br>




