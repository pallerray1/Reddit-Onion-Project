# Reddit Classification Project

### Raymond R. Paller,  DSI-US-9-Chicago


### Problem Statement

To assemble posts from two chosen subreddits, which in turn serves as feedstock to train a classification model that has the capability to bucketize according to a posting’s origin.


### Executive Summary

To gather and use data to make informed decisions and guide behavior is the raison d'etre for data science.  In this case,
the end objective was to predict where of two possible origins did a document eminate from.  The combined underlying techniques
of data acquisition, language processing, and classification have wide applicabilty since a tremendous proportion of human
communication is written.  Users would include, but are not limited to, individuals, institutions such as education,
commercial and industrial enterprises, and governmental units of many stripes that are seeking to accomplish their
objectives.

In this particular project, the two possible origins for documents were the subreddit postings from "The Onion" and
"not the onion".  They were chosen because, though they are from different organizations, they had substantial enough
overlap to make the attempt to differentiate between the two both challenging yet doable (with the additional benefit of
fun content).

Data was obtained by using an API to access Pushshift.io that in turn had accessed and collected Reddit posts.  5,000 posts
from each were obtained.  The data used was a given post's title only.  The nature of The Onion and not the onion subreddits
are such that a post's body was nonexistant except for an underlying URL to access the full article that was either maintained
at The Onion itself, or actually often more frequently, a third party news organization such as CNN, ABC News, Fox, local newspapers, and the like.  Including the underlying URL article content was not used since news articles themselves were
long (compared to many/most other subreddit's body lengths) and would become unwieldy at the 5,000 posts level.  In addition,
the style and characterizations of The Onion and not the onion would be miscolored by the wording presence of the outside
third party news organizations.  Other posting data was obtainable but not used.  An example would the URLs themselves and
time stamps, which would really fall under the domain of traffic analysis and not be really in the spirit of an NLP oriented
project.

The approach to modeling was to employ sentiment analysis, word vectorization, and feature engineering to create datasets.
The datasets were then examined using a wide variety of classification models.  Metric utilized to gauge effectiveness was
accuracy.


### Conclusions and Recommendations

Excellent but short of perfect results were obtained by using a model utilizing Multinomial Naive Bayes with TFIDF.  
Other models, including many that were more complex, were attempted, but meaningful gains were not made.  As seemingly
always, additional improvements can be made.


Key points:

* The accuracy score was extremely high for training data, and fell when testing data and cross validation were used.
Such overfit led to some regularization attempts, but the regularized models performed even worse.  

* Most models (based on the test and cross validation scores) came in at the very, very low 80s for accuracy.  The very
best was Multinomial Naive Bayes with TFIDF coming in at a little over 84%.  An accuracy wall was hit.  Attempts to
breach this wall by changing both word vectorization methods and counts,  feature engineering,  and tuning model
hyperparameters were made but didn't push the trench far.

* Improvements that can be made would include a customized stop word list.  In tuning the models, using pre-packaged
stop words lists NEVER came out as a best parameter.  Upon conferring with colleauges afterwards, others obtained
favorable results utilizing a prepackaged stop word list that had added to it words that were common in their specific
document domains.


### Notebooks

---
**Best Performing Model: TFIDF with Multinomial Naive-Bayes**
* [TFIDF with Multinomial Naive-Bayes with GridSearch](code/code_for_models/tfidf_with_multi_naive_bayes_with_gridsearch_tuning.ipynb)

---
**The remaining models utilized**

* [SIA Vader Alone w/o Word Vectorization (run on plain Logistical Regression)](code/code_for_models/vaderized_sai_both_perform_and_run_alone.ipynb)
* [Count Vector/SIA Vader with Logistic Regression](code/code_for_models/count_vector_and_vaderized_sia_with_logistic_regression.ipynb)
* [Count Vector/SIA Vader/PolyFeature Engineering with Logistic Regression, Lasso, Ridge, and ElasticNet](code/code_for_models/count_vector_vaderized_sia_poly_feature_eng_with_logistic_regression_and_lasso_ridge_elasticnet.ipynb)
* [Count Vector with Multinomial Naive-Bayes with GridSearch](code/code_for_models/count_vector_with_multi_naive_bayes_with_gridsearch_tuning.ipynb)
* [TFIDF with Ada(DecisionTress)/GradiantBoost/DecisionTrees/KNearestNeighbor inside Voter with GridSearch](code/code_for_models/tfidf_with_ada_gb_dt_knn_inside_voter_with_gridsearch_tuning.ipynb)
* [TFIDF with Ada(DecisionTrees)/GradiantBoost inside Voter with GridSearch](code/code_for_models/tfidf_with_ada_gb_inside_voter_with_gridsearch_tuning.ipynb)
* [TFIDF with Gaussian Naive-Bayes](code/code_for_models/tfidf_with_gaussian_naive_bayes.ipynb)
* [TFIDF with Logistic Regression with GridSearch](code/code_for_models/tfidf_with_logistic_regressions_with_gridsearch_tuning.ipynb)
* [TFIDF with Random Forest with GridSearch](code/code_for_models/tfidf_with_random_forest_with_gridsearch_tuning.ipynb)

**Data Acquistion**
* [Reddit Data Acquistion Utilizing Wrapper API onto Pushshift](code/code_for_data_acquisition/reddit_data_aquisition.ipynb)

**Utilites**
* [Plot Generatior for Presentation Slides](code/code_for_utilities/graphs_generator.ipynb)
* [Racetrack for Model Crash Testing](code/code_for_utilities/model_testing_crash_test_dummy_racetrack.ipynb)

---
**Datasets**
* [Data Frame Complete Containing 5,000 Posts Each from "The Onion" and "not the onion"](datasets/df_onion_not_onion.csv)
* [Data Frame Complete After Sentiment Scores Add-On](datasets/df_vaderized.csv)

---
**Presentation**
* [Slide Deck: Tripping Down Classification Road](Tripping_Down_Classification_Road.pdf)

