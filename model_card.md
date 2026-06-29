# Model Card: Mood Machine

This model card is for the Mood Machine project, which includes **two** versions of a mood classifier:

1. A **rule based model** implemented in `mood_analyzer.py`
2. A **machine learning model** implemented in `ml_experiments.py` using scikit learn

## 1. Model Overview

**Model type:**  

I compared both the rule based model and the ML model.

**Intended purpose:**  

The models both try to classify a short text messages by its moods into four catergories: positive, negative, neutral, or mixed.

**How it works (brief):**  

For the rule based version. A score of +1 is add if the word is positive, and -1 if the word is negative. If there is a negation word prior, then the score is inverted.

The ML version is trained in 1000 iterations on the sample sentences and their corresponding labels.



## 2. Data

**Dataset description:**  

There are 11 posts total. I added 5 posts that focuesed on sarcasm and slang and a emoji.

**Labeling process:**  

There wasn't any hard post to label. Additionaly, if there were any, they can be label as "mixed" since it is a catch-all label.

**Important characteristics of your dataset:**  

- Contains slang or emojis  
- Includes sarcasm  
- Some posts express mixed feelings  
- Contains short or ambiguous messages

**Possible issues with the dataset:**  
Think about imbalance, ambiguity, or missing kinds of language.

This dataset is really small, only 11. The slang used are mainly Gen-Z so different slang might not be categorize correctly.

## 3. How the Rule Based Model Works (if used)

**Your scoring rules:**  
Describe the modeling choices you made.  
Examples:  

- Positive and negative words +1 and -1 to the score respectively.
- Negation word before the a positive or negative word invert the score
- No weighted words  
- No Emoji handling  
- Threshold decisions for labels:
    - Positive if score >= 1
    - Negative if score <= 1
    - Neutral if score == 0
    - No mixed currently

**Strengths of this approach:**  
Where does it behave predictably or reasonably well?

**Weaknesses of this approach:**  

Sarcasm, subtlety, mixed moods, unfamiliar slang all caused the rule based classifier to fail.

## 4. How the ML Model Works (if used)

**Features used:**  
Describe the representation.  
Example: “Bag of words using CountVectorizer.”

**Training data:**  
State that the model trained on `SAMPLE_POSTS` and `TRUE_LABELS`.

**Training behavior:**  
Did you observe changes in accuracy when you added more examples or changed labels?

**Strengths and weaknesses:**  
Strengths might include learning patterns automatically.  
Weaknesses might include overfitting to the training data or picking up spurious cues.

## 5. Evaluation

**How you evaluated the model:**  
Both versions can be evaluated on the labeled posts in `dataset.py`.  
Describe what accuracy you observed.

**Examples of correct predictions:**  
Provide 2 or 3 examples and explain why they were correct.

**Examples of incorrect predictions:**  
Provide 2 or 3 examples and explain why the model made a mistake.  
If you used both models, show how their failures differed.

## 6. Limitations

Describe the most important limitations.  
Examples:  

- The dataset is small  
- The model does not generalize to longer posts  
- It cannot detect sarcasm reliably  
- It depends heavily on the words you chose or labeled

## 7. Ethical Considerations

Discuss any potential impacts of using mood detection in real applications.  
Examples: 

- Misclassifying a message expressing distress  
- Misinterpreting mood for certain language communities  
- Privacy considerations if analyzing personal messages

## 8. Ideas for Improvement

List ways to improve either model.  
Possible directions:  

- Add more labeled data  
- Use TF IDF instead of CountVectorizer  
- Add better preprocessing for emojis or slang  
- Use a small neural network or transformer model  
- Improve the rule based scoring method  
- Add a real test set instead of training accuracy only
