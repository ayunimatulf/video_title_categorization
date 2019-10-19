# video_title_categorization
Developing a Logistic Regression model which can categorize videos t0 5 class ('sport', 'tech', 'politics', 'games', and 'lifestyle')
## DATASET
Dataset include 5 categorical text, there are 'sport', 'tech', 'politics', 'games', and 'lifestyle'. Number of videos titles is 88960. Percentage of data is represent in the diagram below.
<p align='center'>
  <img src='https://github.com/ayunimatulf/video_title_categorization/blob/master/data_digaram2.png'>
</p>

From the diagram we know that number of data in each category is better then the SARA data before. So I choose to just using the original dataset for classification the data

## DISCUSSION
In this discussion that will be split as 3 process, pre-processing data, prediction method, and implementation model.
1. Pre-processing data
    1. Import dataset and rewrite as pandas DataFrame with the label where I use 1, 2,3, 4,5 for represent 'sport', 'tech', 'politics', 'games', and 'lifestyle' category respectively.
    2. Then clean the data from non-letters characters, setting lower case in each sentence, and removing stopwords
    3. Create wordclouds from each categorical data to know what the frequent words appear in each category
    4. After that create doc-by-term matrix to represent each sentence as numerical vector, if A_(m×n) is doc-by-term matrix so each element in a_ij represent how many term_j appear in document_i
    5. Weighting each elements in matrix a using TF-IDF, the purpose of this step is to reflect how important a term is to a document in a collection or corpus.
2. Prediction method
  Create the logistic regression model linier_model.LogisticRegression from sklearn. Set the multi_clas=’multinomial’, it’s mean that the class that we used is multiclass where the probabilities function that used for the classify is Softmax Function where usually known as ‘Multinomial Logistic Regression’ or ‘Softmax Regression’. The parameter is algorithm that used in the optimization problem. I used ‘sag’ or Stochastic Average Gradient descent solver as faster for large ones based on sklearn documentation. I also trying ‘saga’ and ‘newton-cg’ but there aren’t significant change in my evaluation metrics. First I training my model using training data and evaluate the data from testing data or validation data. 
3. Model Implementation
After I think I have the best model that I can raise I implemented the model for text input to knowing the text I have input is SARA or a normal one. The step is explained bellow :
    1. First I save my TF-IDF values from my dataset before so I can transform my new text to new doc_by_term matrix using old TF-IDF values
    2. Input a text
    3. Clean the text from non-letter characters, setting lowercase, and remove stopwords
    4. Transform the text to doc_by_term matrix using old TF-IDF values
    5. Then I predicting the matrix using my model I have created
## RESULT
The evaluation metrics from the data is represents below :
<p align='center'>
  <img src='https://github.com/ayunimatulf/video_title_categorization/blob/master/evaluation_metrics.png'>
</p>

From the evaluation metrics we know that the model has great performance where the accuracy is 0.96 and the value of each evaluation parameters (precision, recall, f1-score) is more than 0.90. Let’s see how the model predict my text input data.
<p align='center'>
  <img src='https://github.com/ayunimatulf/video_title_categorization/blob/master/output_2.png'>
</p>

