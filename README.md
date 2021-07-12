<!-- <img align="center" alt="banglaLM" src="assets\data-original.png" width="100%" /> -->

# Bangla FastText Model & Toolkit
We have constructed a dataset that contains Bangla text data for training unsupervised ML model, and it contains around 14 GB of text data. One of the largest in Bengali Language model called `BanglaLM: Bangla Language Model Dataset`. The Bangla FastText model had been developed based on this dataset. We used google cloud to train model. We developed two models based on skipgram and cbow training method. This is open source python module to use these two models easily. We also developed sentence embedding systems for the using of sklearn classifiers. It showed better perfromance than facebook pretrained fasttext model on Bangla Wikidataset.
## Dataset (Bengali)

### Link for the dataset :
-> Github: [BanglaLM: Bangla Corpus For Language Model Research](https://github.com/Kowsher/BanglaLM-Dataset)

-> Kaggle: [BanglaLM: Bangla Corpus For Language Model Research](https://www.kaggle.com/gakowsher/bangla-language-model-dataset)

### Model link:
[Bangla FastText](https://www.kaggle.com/gakowsher/bangla-fasttext)



## Installation
To install the latest release, we can do :

``` python
!pip install BanglaFastText
```
or, to get the latest development version of BanglaFastText, we can install from our github repository :
``` python
$ https://github.com/Kowsher/Bangla-Fasttext.git
$ cd Bangla-Fasttext
$ sudo pip install .
$ # or :
$ sudo python setup.py install
```
For further information and introduction see README.md

## Getting started

In order to learn word vectors, as described here, `BanglaFastText` function like this:
``` python
import BanglaFastText

#There are two variations of training methods cbow and skipgram. By default, it's cbow method and the model preparation path is set default as current working directory 
>>> Bn = BanglaFastText.BanglaFasttext()

#If want to save the model in manual path, we can by using 'sav_path' parameter.

# Skipgram model :
>>> Bn = BanglaFastText.BanglaFasttext(method='skipgram', save_path = './content/model')
# 'path' is the directory to save the downloaded model
>>> model = Bn.model_load()

# or, cbow model :
>>> Bn = BanglaFastText.BanglaFasttext(method='cbow', save_path = './content/model')
>>> model = Bn.model_load()
```
Where  `method parameter is to choose the training method and path is to save model.`

## Loading a model object
If we have already model then we can simply read and load the model as :

``` python
# To read a model
>>> Bn = BanglaFastText.BanglaFasttext(model_path = './model_name')

# to load the model as object we can
>>> model = Bn.model_load()
```
## Playing with the parameters
``` python
# to get vector of a word
>>> model['দেশ']

# to get most similar words
>>> model.most_similar("দেশ")

# to find word similarity
>>> Bn.word_similarity('কিতাব', 'বই')

# to find sentence similarity
>>> Bn.sent_similarity('আমি দেশকে ভালোবাসি', 'অনেক সুন্দর আমাদের দেশ')

#  for sentence embedding 
>>> corpus = ['আমি দেশকে ভালোবাসি', 'অনেক সুন্দর আমাদের দেশ']
>>> X = Bn.sent_embd(corpus)
```
## Fine Tuning
 If we want to fine tuning or update weights by our dataset
``` python
>>> corpus = ['আমি দেশকে ভালোবাসি', 'অনেক সুন্দর আমাদের দেশ']
>>> Bn.fine_tuning(corpus, epochs=5)
>>> model = Bn.model_load()

......
>>> tuned_model = Bn.fine_tuning(corpus, epochs=5) # to get the raw model after finetuned, if we want to use it further  
```
