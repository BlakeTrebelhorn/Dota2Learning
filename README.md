# Dota 2 Learning
I found this data set on the UCI machine learning data base (https://archive.ics.uci.edu/ml/datasets/Dota2+Games+Results#)
A few of my good friends play this game, and I wanted to try some machine learning so I wound up using this data set. 
The data already comes split into a testing and training set, with 2 separate csv files. I decided to use the training set
	for training as well as validation, before using on the testing set at the end. I will use Scikit-learn and it's modules,
	as it's what I'm most familiar with.

The first classifier I tried was the Random Forest Classifier (RFC), as this one usually does well out of the box. On it's first run
	the RFC got an accuracy of about 54%, which is slightly better than guessing, but not by much. After a small amount of tweaks,
	I quickly realized that ther RFC would not be a good classifier because of it's nature (ha! get it?). The RFC takes subsets of the
	features (columns) of the data. Many of these columns contain zeros, which would build useless trees. 

I next tried the Perceptron. I thought a little more before using this algorithm. Perceptrons learn by taking each feature and assigning
	weights, which eventually makes a linear separator. After initial testing, the Perceptron was reporting around 91% accuracy, a great
	over the RFC, and much better than random. After some tweaking, the Perceptron reporting about the same accuracy. Because of the high
	accuracy reported, I realized I may have a linear data set.
