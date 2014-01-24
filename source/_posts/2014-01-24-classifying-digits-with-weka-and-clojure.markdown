---
layout: post
title: "Classifying Digits with Weka and Clojure"
date: 2014-01-24 12:15
comments: true
categories: 
---

I was looking to get my feet wet with Machine Learning and I decided to try out the Kaggle's [Digit Recognizer problem](http://www.kaggle.com/c/digit-recognizer). 
The goal is to recognize hand written digits. You are provided with a training set that contains the label (0-9) and the pixel values of a 28x28 image. So, every row
in the training set is contains a label and 784 numbers each of which contains a value from (0-255) in grayscale.

I used the [Weka 3](http://www.cs.waikato.ac.nz/ml/weka/) [RandomForest](http://weka.sourceforge.net/doc.dev/weka/classifiers/trees/RandomForest.html) classifier. 
It implements the Breiman, et al's [RandomForest](http://www.stat.berkeley.edu/~breiman/RandomForests/cc_home.htm) method for classification. 
I downloaded the training and test data set from Kaggle. I had to change the `train.csv` to change the labels to strings. So the file looks a bit
like below. It was a simple enough change so I did that in vim. I used the test csv unchaged.

```
label, pixel1, pixel2, pixel3, ...
"Zero", 0, 0, 0, ....
"One", 0, 0, 0 ...
```

You can find the code on the [random-forest](https://github.com/vagmi/random-forest) github repo. With 10 trees and 28 random features, I got a 94%
accuracy while with 100 trees, the accuracy improved marginally to 96%.

What is powerful about this technique is that it does not know anything about the domain that we are dealing with. As I followed the discussions on
the Kaggle forums, people have got better predictions by processing the original [MNIST](http://yann.lecun.com/exdb/mnist/) training set which contains 
more samples. So better data beats clever algorithms. Off to solve more Kaggle problems now.
