# Dota 2 Learning
I found this data set on the UCI machine learning data base (https://archive.ics.uci.edu/ml/datasets/Dota2+Games+Results#)
A few of my good friends play this game, and I wanted to try some machine learning so I wound up using this data set. 
The data already comes split into a testing and training set, with 2 separate csv files. I decided to use the training set
	for training as well as validation, before using on the testing set at the end. I will use Scikit-learn and it's modules,
	as it's what I'm most familiar with.

The first classifier I tried was the Random Forest Classifier (RFC), as this one usually does well out of the box. On it's first run
	the RFC got an accuracy of about 54%, which is slightly better than guessing, but not by much.