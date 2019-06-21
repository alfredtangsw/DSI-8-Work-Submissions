# <span style="color:green"> Project 3</span>

Alfred Tang
<br>General Assembly Singapore
<br>Data Science Immersive 8

# <span style="color:green">Project Objectives</span>
- Select 2 subreddits and query their APIs for post text
- Combine post text from the 2 subreddits into 1 dataset and classify them
- Use at least 2 models. 1 model must be a Naive Bayes model.

# <span style="color:green">Problem Statement</span>
- Which text belongs to which subreddit?
- Which model is best for classifying the text according to their subreddits?

# <span style="color:green">Executive Summary</span>
### Subreddit selection
2 highly similar subreddits were selected: DaveRamsey and personalfinance.

Dave Ramsey is a person who has devised his own method for dealing with personal financial crises such as debts, and the subreddit users follow his methodology.

personalfinance is a subreddit where people openly request advice and discuss their financial issues.

The two highly similar subreddits were selected to help me appreciate the power of different classification models, as a previous selection of r/personalfinance vs r/writing produced models that had accuracy in excess of 0.93 at the baseline level with MultinomialNB and 0.99 with Logistic Regression. 

It would be difficult, if not impossible, to illustrate the effectiveness of other models beyond that point.

|Class |Class %|
|-----|-----|
|DaveRamsey|    0.511749|
|personalfinance|    0.488251|

### Common Words

<p style="text-align: center;">Titles</p>
<img src="images/reddit_titles_wordcloud.png">

<p style="text-align: center;">Posts</p>
<img src="images/reddit_posts_wordcloud.png">

### Modelling
4 models were selected: Multinomial Naive Bayes, Logistic Regression, Support Vector Machine, and Stochastic Gradient Descent Classifier. 

Both Title and Post text were used for analysis, but the accuracy of title classification was low across the board (below 0.75) and post text was chosen instead because of higher classification accuracy.

The data proved sufficienty challenging for the models; they did not present overly high accuracy at the baseline (baseline Naive Bayes accuracy was 0.862).

Parameters were tuned through GridSearchCV. Tuning proved effective, as it raised the accuracy of most models, most significantly the LogisticRegression model.

In this case, Logistic Regression provided the best accuracy of all selected models: 0.881 accuracy, outperforming Naive Bayes' 0.8768 (the 2nd highest accuracy).

|Model |	Baseline	|GridSearchCV|	Tuned|
|----|----|----|----|
|MultinomialNB	|0.862213|	0.864903|	0.876827|
|LogReg	|0.862213|	0.858635|	0.881002|
|Support Vector Machine|	0.853862|	0.852368|	0.866388|
|Stoch Grad Desc|	0.820459|	0.853064|	0.874739|

# <span style="color:green"> Findings</span>

- It is possible that with a larger dataset, the Logistic Regression may output higher accuracy or sustain higher accuracy than other models. 

- The Naive Bayes model was simple but effective in all 3 phases of modelling. It is known for outputting good accuracy even with small datasets.

- **Title best n_grams** was consistently (1,1) whereas **Post best n_grams** ranged from (1,2) to (1,4). (Highest n-grams gridsearched was (1,5))

# <span style="color:green"> Further tweaking and improvement</span>

- Try different max_features for the vectoriser
- Add subreddit names as stopwords
- Change Baseline
- Severe train-step overfitting problems discovered -- need to tune again