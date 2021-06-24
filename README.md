<img align="center" alt="banglaLM" src="assets\data-original.png" width="100%" />

# Bangla FastText Model & Toolkit
We have constructed a dataset that contains Bangla text data for training unsupervised ML model, and it contains around 14 GB of text data. One of the largest in Bengali Language model called `BanglaLM: Bangla Language Model Dataset`. The Bangla FastText model had been developed based on this dataset. We used google cloud to train model. We developed two models based on skipgram and cbow training method. This is open source python module to use these two models easily. We also developed sentence embedding systems for the using of sklearn classifiers. It showed better perfromance than facebook pretrained fasttext model on Bangla Wikidataset.
## Dataset (Bengali)

### Kaggle link for the dataset :
[BanglaLM: Bangla Language Model Dataset](https://www.kaggle.com/gakowsher/bangla-language-model-dataset)
### Model link:
[Bangla FastText](https://www.kaggle.com/gakowsher/bangla-fasttext)



# Installation
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

# Getting started

In order to learn word vectors, as described here, `BanglaFastText` function like this:
``` python
import BanglaFastText

#there are two variation of training methods cbow and skipgram. 

# Skipgram model :
>>> Bn = BanglaFastText.BanglaFasttext(method='skipgram', path = './content/model/')
# 'path' is the directory to save the downloaded model
>>> model = Bn.model_load()

# or, cbow model :
>>> Bn = BanglaFastText.BanglaFasttext(method='cbow', path = './content/model/')
>>> model = Bn.model_load()
```
Where  `method parameter is to choose the training method and path is to save model.`

## Loading a model object
If we have already model then we can simply read and load the model as :

``` python
# To read a model
>>> Bn = BanglaFastText.BanglaFasttext(model_name = 'model_name')

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
>>> corpus = ['আমি দেশকে ভালোবাসি', 'অনেক সুন্দর আমাদের দেশ']
>>> fine_tuning(self,corpus, epochs=5)
>>> model = fine_tuning(self,corpus, epochs=5) # to get the model after finetuned 
