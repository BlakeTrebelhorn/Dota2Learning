# Dota 2 Learning
## Intro
I found this data set on the UCI machine learning data base (https://archive.ics.uci.edu/ml/datasets/Dota2+Games+Results#)
A few of my good friends play this game, and I wanted to try some machine learning so I wound up using this data set. 
The data already comes split into a testing and training set, with 2 separate csv files. I decided to use the training set
	for training as well as validation, before using on the testing set at the end. I will use Scikit-learn and it's modules,
	as it's what I'm most familiar with.
## Random Forest
The first classifier I tried was the Random Forest Classifier (RFC), as this one usually does well out of the box. On it's first run
	the RFC got an accuracy of about 54%, which is slightly better than guessing, but not by much. After a small amount of tweaks,
	I quickly realized that ther RFC would not be a good classifier because of it's nature (ha! get it?). The RFC takes subsets of the
	features (columns) of the data. Many of these columns contain zeros, which would build useless trees. 
## Perceptron
I next tried the Perceptron. I thought a little more before using this algorithm. Perceptrons learn by taking each feature and assigning
	weights, which eventually makes a linear separator. After initial testing, the Perceptron was reporting around 56-58% accuracy, about
	the same as the RFC. Even some tweaking resulted in the same numbers.
## A day's work
I quickly added a Multilayer Perceptron and 2 different kerneld SVMs, but it was time to call it a day.
## Starting up the next day, and Naive Bayes
Upon returning to my work, I added some Naive Bayes objects. The Bernoulli and Gaussian didn't perform as well as I'd hoped, so I tried Multinomial.
	I ran into an error: `ValueError: Input X must be non-negative` I had forgotten that my data contained values of -1 for indicating which team 
	chose which hero. I had to figure out how to transform the data for MNB to work.
### Transforming the data for Multinomial Naive Bayes
Using the MinMaxScaler from Scikit-learn, this was actually pretty easy. It takes the data and scales it to lie within a range, with the default being
	(0,1). It outputs a numpy array, which we can turn back into a pandas dataframe for our Multinomial Naive Bayes algorithm. After fixing the data
	and testing it on the MNB, it performed quite poorly, with accuracies around 52%. Queue "wah-wah-wah" sound effect.
## Support Vector Machine
So back to my code from the previous night, the support vector machines. From experience these take a while to build. I imported `time` into python
	so I could measure how long this was taking. After my first SVM ran, it took 17 minutes alone to train! And of course I ran into an error because
	of a typo in my code, so it had to rerun again. Realizing this takes a while, I imported joblib into my code so I can export my trained model
	once I'm done with it, so I won't have to retrain each time.
### Training Support Vector Machines
This takes a long time. The default RBF kernel as well as the sigmoid kernel both take around 20 minutes to train. But the linear kernel took nearly 2 
	to train! I'm glad I imported joblib so I can dump my trained linear kernel for later.
## Back to training SVMs
So I'm back at it with the Support vector machines. I loading in my pickled linear SVM and tested it, and it still had an accuracy of about 59% like 
	before. I'd like to continue working with this one, but ~2 hours for training is a bit to long right now. So I'll try to speed it up - using PCA!
## Principle Component Analysis
Took a break from this - I worked on implementing other kernels in the SVMs.
## Linear and Polynomial SVM
After tweaking the `C` value of the linear kernel SVM, it trained a lot faster. It also got a bit more accurate - ~60% so far. I also tried a basic
	polynomial kernel, which took about 5.1 hours to train. This one will need some tweaking to fix.
## Polynomial Kernel, KNN, and Logistic Regression
Wow. Polynomial takes a long time to run. I tried a few different `C` values today with it and pickled them. They got fairly good results, ~58%. I also
	wanted to try Logistic Regression, as well as K Nearest Neighbor. I thought K Nearest Neighbor would do better because of the nature of the data, but
	it didn't do too well in testing. I think from this point forward I will be focusing in on the algorithms that did well and try to peak their performance.
## Summary of another day's work
I reloaded my pickled kernels from the previous days works. I found the highest performing Linear and Polynomial kernels, and will work on those later. In the 
	meantime, I've worked on optimizing the Logistic Regressor model, as well as the Multilayer Perceptron model. I did so using Grid Search, which allows me
	to pass in multiple values for certain parameters, and tests all of them and returns the best combination. I've gotten both the Logistic Regressor and 
	Multilayer Perceptron very close to 60%.
