# Spam Classifier (Naive Bayes + TF-IDF)

## What this project does
Classifies SMS messages as spam or ham (not spam) using a Naive Bayes 
classifier trained on TF-IDF features extracted from message text.

## Dataset
[SMS Spam Collection Dataset](link) — 5,572 labeled SMS messages 
(~87% ham, ~13% spam).

## Approach
1. Cleaned and renamed raw CSV columns
2. Split data into train/test sets **before** vectorizing, to avoid 
   data leakage (the vectorizer should never see test data during fitting)
3. Converted text to numeric features using TF-IDF, which weighs words 
   by how frequent they are in a message vs. how rare they are overall — 
   so distinctive spam words (e.g. "free", "winner") get more weight than 
   common filler words
4. Trained a Multinomial Naive Bayes classifier
5. Evaluated using accuracy, precision, and recall — not just accuracy, 
   since the dataset is imbalanced (~87% ham) and a model that always 
   guesses "ham" would already look 87% accurate while being useless

## Results
- Accuracy: 0.968609865470852
- Precision: 1.0
- Recall: 0.7651006711409396
- Confusion Matrix:
 [[966   0]
 [ 35 114]]

## What I learned
- Why splitting data *before* vectorizing matters (avoiding data leakage)
- Why accuracy alone is misleading on imbalanced datasets
- How TF-IDF and Naive Bayes work together for text classification
