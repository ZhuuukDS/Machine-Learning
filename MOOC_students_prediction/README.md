# MOOC_students_prediction

### Machine Learning test problem to predict whether a student will finish the course or not


### Description

The problem is the following - we need to predict whether a student of MOOC is going to successfully finish the course or not based on the first 2 days of his course studying.

We assume that student is going to finish course if he/she has successfully solved more than 40 practical problems (steps).

We are given a data:

* ***submissions_data_test.csv***
* ***event_data_test.csv***

where an information about solutions and actions of 6184 students for the first 2 days of studying stored.

For model training we have the following datasets:

* ***submissions_data_train.csv***
* ***event_data_train.csv***

with historical information about the students attended the course.


Using data from the first two days of activity in a course, we need to predict whether a user will score over 40 points in a course or not.

### Results format

The result of this problem is a [my_predict_0.87655.csv](/data/result/my_predict_0.87655.csv) file with prediction for each user from the test data. Located in *data/result* folder.

So, it is a dataframe with probabilities to score more than 40 points for all 6184 students.

The aim is to find a set of parameters and features to maximize ROC-AUC score of the model.



### Data structure

* [event_data_train.csv](/data/raw/event_data_train.zip) / [event_data_test.csv](/data/raw/event_data_test.csv) - information about actions that students perform on the practical tasks (steps)
    * **step_id** - step id
    * **user_id** - anonymized user id
    * **timestamp** - time of action performed in unix date format
    * **action** - action with possible values:
        * _discovered_ - user moved on a step
        * _viewed_ - step viewed,
        * _started_attempt_ - user started an attempt to solve the step (pressed the button 'start', but not yet submitted)
        * _passed_ - step successfully solved

* [submissions_data_train.csv](/data/raw/submissions_data_train.zip) / [submissions_data_test.csv](/data/raw/submissions_data_test.csv) - information about time and status of submits
    * **step_id** - step id
    * **timestamp** - time of submit in unix date format
    * **submission_status** - status of submit ('correct', 'wrong')
    * **user_id** - anonymized user id


Solution is in the [mooc_user_model.ipynb](/reports/mooc_users_model.ipynb) file or [pdf](/reports/mooc_users_model.pdf) version. 

[RandomForest из sklearn](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) is used as a model.


### Project Strucuture

```
├── data                  <- folder with data
│   ├── raw               <- original data
│   ├── processed         <- final data sets for modeling
│   └── result            <- output .csv file with results
├── notebooks             <- Folder with Jupyter notebooks
│   ├── exploratory       <- Jupyter notebooks with initial explorations
│   └── final             <- polished work for reporting
└── reports               <- generated analysis as HTML, PDF
```



