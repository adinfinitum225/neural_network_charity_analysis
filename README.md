# Neural Network Charity Analysis

## Overview

The purpose of this analysis is to train and apply a neural network machine learning model to determine quality candidates for investment funds. The dataset includes organization information, application type, and funding amount requested. 

## Results

### Data Preprocessing

* The target is whether or not the funded organization was able to effectively utilize the funds.
* The feature variables of the model are the application type, affiliation, organizaiton classification, organization industry, use case for funding, status, income amount, and whether the application has any special consideration.
* The unnecessary variables are the organization name and application ID. Since they are unique to each row they will have no effect on the model.

### Compiling, Training, and Evaluating

* Initially I chose two hidden layers with the ReLU activation function. I chose two layers to keep things simple at first and avoid the risk of immediately overfitting. The ReLU activation function was chosen due to the suspected non-linearity of the the relationships in the data. 
	* The first layer was given 80 neurons since the input dimension was rougly 40 after one-hot encoding. 
	* The second layer was given 30 neurons to reduce chance of overfitting.
* Unfortunately I was not able to achieve the target model performance, with a testing accuracy of only 72.76 percent
* In order to increase model performance I tried three different methods. Two focused on the asking amount for funding because that had an extremely skewed distribution. The last method I tried was hyperparameter tuning using Keras.
	* First I tried binning the ask amount into '5000' and 'other' since the majority of ask amounts were for 5000. This was able to slightly increase accuracy to 73.22 percent
	* My second approach was to perform Winsorization on ask amounts that were greater than three times the interquartile range plus the third quartile. This had little to no effect and the accuracy was 72.27 percent.
	* Lastly I performed automate hyperparameter tuning. This ended up with 5 hiddent layers, and an accuracy of 73.00 percent.

## Summary

Overall this deep learning model seemed to be only moderately successful. It would need additional work to be able to reliably predict good charity investment opportunities. Since most of the variables are categorical a chi-squared test should be perfromed to identify any variables that don't correlate with the target, and remove them from the features. Additionaly a logorithmic transformation could be applied to the ask amount since it is such a skewed distribution. 
Before performing these steps I would probably take a step back and try a random forest classifier to see how it performs. Given the categorical nature of the features I suspect it would perform better than a simple neural network.
