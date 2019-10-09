+++

title =  "PharmEazy Search"
+++

<h1>A Text Search Module using Python</h1>

Search engines play a major role in our day to day activities. Instant information, and we all turn to Google or Yahoo. Search engines have become an essential part of our lives. Here, a simple search engine has been developed for a drug dataset.

The dataset used for this has been taken from [Kaggle](https://www.kaggle.com/jessicali9530/kuc-hackathon-winter-2018/home).
This dataset consists of patient reviews for numerous drugs that have been prescribed for the symptoms that they have experienced, and how effective they have been.

The code was coded initially on Jupyter Notebook to have a stepwise visual response of the code flow.
The code was finalized on Notepad++.

Any other text editor will do just fine as long as they support the Python libraries that are being used.

For the application, Flask was used.

<br>

<h2>Data Preprocessing:</h2>


In order to create a text search module, first we need to have the appropriate dataset that we intend to work on.
On obtaining the data set, the dataset has to be processed, and brought to a comprehendable form.

Preprocessing of data of a large data set is a task, especially when it contains entries more than 100k. In the dataset that I have used, there are html codes that are present in place of special characters. For this, the unescape function of the html library has been used.

Text search will be performed  on the reviews column of the dataset, which contains long length of words. These words are separated from the string with the help of Python's split function.

In order to make the search more generalized, all characters have been converted into lowercase letters.

Next, we use the nltk library, which is probably one of the most useful libraries for natural language processing in Python. We import the stopwords function from the corpus of the module. We can utilize this to eliminate the stopwords that are present in the data. On completing this, we use the lemmatizer funtion in order to identify the root of the words, broadening the spectrum for the search. 


<br>

<h2>Word Bank Creation:</h2>


In order to make sure the search engine covers all the words that are present in the dataset, we have to create a word bank, which contains all the unique words that are present. The data structure that can be used for this is a python dictionary. This makes use of hash indexing, which is quick.

For each review, i.e document, we have to create a posting list, and this is possible by calculating the TF-IDF of the document.
(Term Frequency - Inverse Document Frequency).
  **Prototype:**
  <pre>
  { word1 : [ df, { id1:[p1, p2, .....], id2:[p1, p2, ....], ....... }, 
            **{ doc1:w1, doc2:w2, .... }** ]
   .
   . 
   .
  }
  </pre>
<br>

<h3> Calculating the TF-IDF weights for each word in the document </h3>
<body>

  1. TF(Term Frequency) of a "word" in a "document":
  <pre>
  TF = frequency of "word" in "document" / total number of words in "document"
  </pre>
  
  2. IDF:
  <pre>
  IDF = total documents in dataset / number of "document"s with "word"
  </pre>
  
  3. TF-IDF:
  <pre>
  TF-IDF = (1+ log(TF)) / (IDF)
  </pre>
  
</body>

<br>

<h2>Query Analysis and Processing:</h2>
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

We take an input from the user through a web application and process the query by calculating the word weight. On doing so, we retrieve the top k results that are required. The cosine similarity is calculated.

$$ {sim(q,r)} = \\vec{q} \\cdot \\vec{d} = \\sum_{t\ \\text{in both q and r}} w\_{t,q} \\times w\_{t,r}.$$

Here, "q" is the query, and "r" is the review, thus, calculating the similarity. 

 If a review is not there in the first k elements, we will utilize weight in the kth element as the upper-bound on weight in the vector. thus finding the upper-bound score.

$$ \\overline{sim(q,r)} = \\sum_{t\\in T_1} w\_{t,q} \\times w\_{t,r}.$$

$$  + \sum_{t\\in T_2} w\_{t,q} \\times \\overline{w\_{t,r}}.$$
