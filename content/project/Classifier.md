+++

title="Review Classification using Naive Bayes Algorithm"

[[gallery_item]]
album = "Screenshots"
image = "hp.png" 
+++

<h1>**Classifiers**</h1>
<body>
The task of classification is the process of predicting a class when a set of data points have been given. This classifier uses a training data to understand
how the variables that are given as input, relate to a certain class. In this project, since we are carrying out classification on the basis of text, the Naive Bayes Classifier is the most appropriate classifier for the sccenario.
Text classification plays a major role in Natural Language Processing as language does not exactly have a fixed schema and there is continuous learning taking place.

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

**Naive Bayes Classifier**
The Naive Bayes Classifier is a classifier that is probabilistic. It is based on the Bayes Theorem, where an assumption is made, that the attributes are conditionally independent.
The classification is carried out by calculating the probability of each given class, and displaying the classes with the highest probabilities as the output.

$$ P(A \mid B) = \frac{P(B \mid A) \, P(A)}{P(B)} $$
</body>

In the given medical dataset that has been downloaded from Kaggle, the column which has the names of the medical condition is going to be predicted with the help of a given review.

In order to carry out the evaluation, the data can be divided into training data, testing data and validation data. In the given dataset, there are two .csv files that are separated as training and testing data.
The validation dataset can be created by extracting it from the bigger training dataset in order to carry out the validation tests.
Here, we will be displaying the accuracy of the classifier.

First, we need to calculate the prior probabilities, and this is done by creating a dictionary which contains the list of all documents,
unique words and total number of words occuring in each class.

dictionary = { class1 : [[review1, review2,.......,reviewn], 
                              [word1, word2,.......,wordn], 
                              tcount],...}

Next, we create another dictionary within, for every class, in which words are keys, and store the frequency value of the word appearing and the number of reviews the word occured in the entire class.

class = { class : [P(class), tcount, ucount,
                              {word1 : [total_no_of_occurances, total_review_count]...}
                          }
                          
For the review: "This medicine was good and effective" for the drug Riboflavin for Migraine(class),
for the word "medicine" in "dictionary" is = [344, 271]. Likewise for "good" it is = [213, 184] and "efficient" is [72,61].


Probablity of a given query belonging to a class is

P(class | word1,word2,word3) = log(P(word1 | class) * P(word1 | class) * P(word1 | class) * P(class))

Probablity of a class is

P(class) = number of reviews in the class / total number of reviews

Probablity of a word1 occuring in a class

P(word1 | class) = (the number of times word1 occurs in class + alpha) / (total number of words in class + total number of words in the vocabulary)

There is just one problem though, suppose if, the conditional probability turns out to be zero, that is, when the word in the query is absent in the vocabulary, then the entire probability becomes zero, that is, which isn't really helpful in terms of classification.
Hence, we use something called the Laplace smoothing, which is used to regularize Naive Bayes. It is denoted as Alpha(the hyperparameter), done by adding 1 to the numerator, which helps in overcoming this problem.

<pre>
P(Migraine) = 0.00769641422969
P(medicine| Migraine) = (344 + 1 )/ (16291 + 21167) = -3.471825444711263
P( good | Migraine ) = (213 + 1) / (16291 + 21167) =  -8.182364822736424
P( efficient | Migraine ) = (72 + 1) / (16291 + 21167) =  -5.295782736465865
</pre>
</body>

**Evaluation and Hyperparameter Tuning**

The Laplace smoothing is the hyperparameter. In case of hyperparameter tuning, the approach around the default was to change the value of the hyperparameter.
Observations show that by decreasing the value of the hyperparameter, the accuracy increased.

{{< gallery album="Screenshots" >}}

The above graph has been plotted between the testing data in order to get the accuracy, and how the change in the hyperparameter(alpha) affects the accuracy. For the values 0.0000001, 0.00001, 0.0001, 0.1, 1, 2, the accuracies obtained were 59.6, 57.4, 55.3, 56.5, 55.7 and 50.4.

**Challenges Faced:**

* The highest accuracy obtained is 59.6% for an aplha value of 0.0000001. The reason why the accuracy is so low is because of the imperfection in the language that has been used in the dataset, and also, as a wide variety of words have been repeated in several different classses.

This means that the text is not exactly unique, thus bringing about an optimized result was fairly a difficult task.

* The conceptual understanding of machine learning classifiers and their way of functioning was a fairly slow process, increasing the time taken to implement the concept.

* Due to the size of the dataset, the training of the model was time consuming.

* The classification results have a lot of common classes, this is because the reviews have all kinds of symptoms mentioned, making it difficult to attain close to perfect results.

**Contributions:**

* None of the predefined libraries were used. The classifier was created with the help of dictionaries and the calculation of probabilities.

* Altering the default value of the Laplace correction, from 1 to various other values, thus making a difference in the accuracy of the classifier model. 

**References:**

* https://towardsdatascience.com/machine-learning-classifiers-a5cc4e1b0623

* https://nlp.stanford.edu/IR-book/html/htmledition/naive-bayes-text-classification-1.html

* https://medium.com/syncedreview/applying-multinomial-naive-bayes-to-nlp-problems-a-practical-explanation-4f5271768ebf

* https://cs.stackexchange.com/questions/3005/smoothing-in-naive-bayes-model


[Click for Phase 3](https://milind.netlify.com/project/image/)


