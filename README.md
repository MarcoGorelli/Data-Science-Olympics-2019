# Data Science Olympics Event, 2019

Here is the notebook with which I made my final submission, where I ranked 16th
out of the 295 competitors who submitted a solution (top 6%).

We were given two datasets (`requests_train.csv`, `requests_test.csv`), a tutorial
notebook which included the custom metric `competition_scorer` and a baseline
submission using an untuned logistic regression model and 3 features. Halfway
through the competition, we were given another two datasets (`individuals_train.csv`
and `individuals_test.csv`).

My approach was simple. I trained an LGBM (Light Gradient Boosting Machine) model on a
subset of the train set using early stopping (with evaluations done on the remaining
part of the train set), predicted on the test set, and submitted. I would normally perform
cross-validation, but due to the size of the dataset (220,000 training rows) and the
very limited amount of time available (2 hours), I only used a single validation set.

I'm genuinely surprised that such a simple solution did well. I attribute this to the following:
- I took great care to ensure that the model's specifications matched those of the
custom evaluation metric (this was given as a hint by the organisers);
- LGBM automatically handles missing variables, categorical variables, and doesn't
require feature rescaling. This allowed me to produce a good solution relatively
quickly.

Had I had more time, I would have taken greater care of feature engineering, understanding
the dataset, and interpreting the model's predictions. I can't understand why `birth_month`
had a high feature importance, and suspect that it may have harmed my score on the test set.
Unfortunately, I lost too much time taking care of the custom evaluation metric, and this
left me little time for feature engineering / data exploration. 
To me, however, a reliable validation scheme is the most important thing, so I'm glad that's
what I prioritised.

I welcome constructive criticism, as long as it's done with the understanding that this
work was done with the competition's 2-hour time-limit in mind :)
