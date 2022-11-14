# Natural Language Processing via Deep Learning
This repository contains the course materials for "Introduction to Natural Language Processing" at Galatasaray University

## Slides

[First week](https://github.com/yasarigno/NLP_Course/blob/3a08e261de1724630088bc6fe94c8057514f3d7b/slides/GSU_WEEK_1.pdf)

## Project - Classification of books by genres

In this NLP project we use neural networks to predict the genre of books by using its summary. We work on a dataset on books downloaded from https://www.kaggle.com/datasets/athu1105/book-genre-prediction

| DATA  |   |
|---|---|
|  number of lines |   4657 |
|  number of columns |   4 |

This project has several versions of notebooks. The aim of this versioning is completely pedagogical. We improve the deep learning model step by step. In more details we have

### Notebook v1

This is the very first version and we do almost **no** preprocessing. 
Word Embedding : GloVe 50d

### Notebook v2

```diff
+ The notebook is more readable with the added comments
+ Section "3. Preprocessing the textual data"
+ Removal of stop-words
+ We try stemming
```

Although we see slight improvement on the accuracy, it is far from being good. 
Notice that because of stemming there are too many words which are not represented in the transfered model, GloVe:

```
Converted 12964 words (7036 misses)
```

In the previous version we had 1822 misses. This may show why it is not a good idea not to apply stemming. 

When you stem a word, say "leaving" or "studies" it is converted into "leav" or "studi". After stemming the new token does not need to be a true word, that is why, it may not be represented in a pretrained model. As a conclusion, it is wise to use lemmatization instead of stemming here.

### Notebook v3

```diff
- GloVe 50d
+ GloVe 300d
```

Using 300d model instead of 50d gives better result in terms of the accuracy on the training set. However the model is not general enough, since the accuracy on the test data is too weak.

### Notebook v4

```diff
- stemming
+ lemmatization
+ 10 more epochs 
```

With lemmatization, there is a bigger number of words which are represented in the pretrained model.

```
Converted 18392 words (1608 misses)
```


We haven't use the callback method yet. But together with the changes above, adding more epoch improved well the model.

| version | Model performance  | comments |
|---|---|---|
|  v1 |   loss: 1.1478 - acc: 0.5899 - val_loss: 1.6672 - val_acc: 0.4765 | |
|  v2 |   loss: 1.0414 - acc: 0.6228 - val_loss: 2.1074 - val_acc: 0.4483 | |
|  v3 |   loss: 0.6292 - acc: 0.7876 - val_loss: 2.1436 - val_acc: 0.4430 | at the 15th epoch |
|  v4 |   loss: 0.3467 - acc: 0.8859 - val_loss: 2.7714 - val_acc: 0.5624 | at the 25th epoch |

---
---

**This project is created for the course MATH410 Natural Language Processing with Deep Learning in the Master Program in Data Science at Galatasaray University.** https://ects.gsu.edu.tr/en/program/index/193

This work is supported by SFEIR https://www.sfeir.com/fr/ 

<img src="https://github.com/yasarigno/NLP_DeepLearning_Course/blob/main/files/sfeir.png?raw=true" width=100>

---

++

+++

++++

+++++

**Credits**

I use course materials from

https://openclassrooms.com/

https://www.coursera.org

https://web.stanford.edu/class/cs224n/
