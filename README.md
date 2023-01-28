# Quora Question Pair Similarity

Over 100 million people visit Quora every month, so it's no surprise that many people ask similarly worded questions. Multiple questions with the same intent can cause seekers to spend more time finding the best answer to their question, and make writers feel they need to answer multiple versions of the same question. Quora values canonical questions because they provide a better experience to active seekers and writers, and offer more value to both of these groups in the long term.  so main aim of project is that predicting whether pair of questions are similar or not. This could be useful to instantly provide answers to questions that have already been answered.
   Credits: Kaggle
### Problem Statement :
Identify which questions asked on Quora are duplicates of questions that have already been asked.

### Real world/Business Objectives and Constraints :
   - The cost of a mis-classification can be very high.
   - You would want a probability of a pair of questions to be duplicates so that you can choose any threshold of choice.
   - No strict latency concerns.
   - Interpretability is partially important.

### Performance Metric:
   - log-loss 
   - Binary Confusion Matrix

### Data Overview:
Train.csv contains 5 columns : qid1, qid2, question1, question2, is_duplicate. Total we have 404290 entries.

### Machine Learning Models:
   - Trained a random model to check Worst case log loss and got log loss as 0.887699
   - Trained some models and also tuned hyperparameters using Random and Grid search.
   - i sampled some data and Trained my models. below are models and their logloss scores.
For below table BF - Basic features, AF - Advanced features, DF - Distance Features including WMD.

| Model         | Features Used | Log Loss |
| ------------- | ------------- | ------------- |
| Logistic Regression  | BF + AF  | 0.4003415  |
| Linear SVM           | BF + AF  | 0.4036245  |
| Random Forest  | BF + AF  | 0.4143914  |
| XGBoost  | BF + AF  | 0.362546  |
| Logistic Regression  | BF + AF + Tf-Idf  | 0.358445  |
| Linear SVM  | BF + AF + Tf-Idf  | 0.362049  |
| Logistic Regression  | BF + AF + DF + AVG-W2V  | 0.3882535  |
| Linear SVM  |  BF + AF + DF + AVG-W2V  | 0.394458  |
| XGBoost  | BF + AF + DF + AVG-W2V  | 0.313341  |

##### References:
1. https://www.kaggle.com/c/quora-question-pairs 
2. https://www.kaggle.com/c/quora-question-pairs/discussion
3. Applied AI Course
4. https://github.com/seatgeek/fuzzywuzzy#usage , https://chairnerd.seatgeek.com/fuzzywuzzy-fuzzy-string-matching-in-python/
5. http://proceedings.mlr.press/v37/kusnerb15.pdf
