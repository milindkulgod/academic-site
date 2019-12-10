+++

title="Image Captioning and Search"
+++

<h1>**Image Captioning and Search**</h1>
<body>

Image captioning works in the realms of Deep Learining. It is the process of generating a textual description of a given image. Deep Learning functions on two major fundamentals, Natural Language Processing and Computer Vision.
This model undergoes two phases, namely training and testing. The training phase is where the image captioning model is trained with a set of images, and a testing set of images is used to test the trained model.
The image will be linked to the corresponding output captions.

The image captioning model uses an attention-based model, which allows us to see the focus area of the image as the caption is generated.
This is where Tensorflow's Keras and eager execution comes into picture. The dataset used for the image captioning model is the MS-COCO Dataset, which is a dataset of images easily accessible by everyone.

After the dataset is downloaded, a subset of the images are selected to train the model. For the preprocessing of images, Inception for classification.

Captions are tokenized to create a vocabulary of all unique words and create a word-index mapping.

The model is then trained. The model architecture is inspired by the Show, Attend and Tell paper.

After training the images, testing images were given as input in order to generate captions for freshly given images as input.



**Next Phase:**

Most of the image captioning was done by the captioning model that was available on the tensorflow github repository, the next task was to use the captions generated as input for a search engine and display images containing the keywords in the caption.

After training the model, a csv file was opened, and, with the help of a for loop, the testing part of the model was made to run for the number of iterations that were equal to the number of images that were being tested.
The caption, along with the url of the image were recorded in a .csv file and the captions were tokenized, bringing it into a suitable format to run it through the search engine, following the same procedure of calculating the TF-IDF scores and displaying the top-k results along with the image.



**Contributions:**

* Altering of the code that was used to test one image into taking in large number of images and storing the created captions in a .csv file.

* Being a photographer, I used some of my personal images in order to generate captions.

* Uploaded images onto a GitHub repository, thus making extraction of the image url easier.



**Difficulties Faced:**

* Usage of a part of the entire dataset did not exactly train the model perfectly, thus generating incomplete or inaccurate captions.

* Even on the Google Colab notebook, training of the model took around 3 hours.

* Timeout of server connections lead to incomplete training of model, and had to be restarted from the first.
  This issue was resolved by using a script that mimicked the action of a mouse click and was run on the browser console, thus keeping the system from being idle for a long time.
  
* Testing the data was also time consuming as the number of captions that had to be generated was big.

* Understanding the concepts of Neural networks, ANN, CNN and Deep Learning in a very short period of time.

* Usage of limited captions resulted in the inaccurate generation of captions. Usage of more data to train will improve the accuracy of the caption to be generated for a given image.



**References:**

* https://github.com/tensorflow/tensorflow/blob/r1.13/tensorflow/contrib/eager/python/examples/generative_examples/image_captioning_with_attention.ipynb

* https://www.tensorflow.org/guide/keras

* https://medium.com/syncedreview/applying-multinomial-naive-bayes-to-nlp-problems-a-practical-explanation-4f5271768ebf

* https://machinelearningmastery.com/develop-a-deep-learning-caption-generation-model-in-python/

* https://towardsdatascience.com/image-captioning-in-deep-learning-9cd23fb4d8d2

* https://www.analyticsvidhya.com/blog/2018/04/solving-an-image-captioning-task-using-deep-learning/

**[Video Link](https://youtu.be/MXC41mWMOWY)**

**[Site Link](https://1dc44174.ngrok.io)**

**[GitHub Link](https://github.com/milindkulgod/DataMiningFall19)**



