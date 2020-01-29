# disaster-tweet-NLP
iPython notebook for [this](https://www.kaggle.com/c/nlp-getting-started) kaggle competition.

The goal is to predict whether tweets are about an actual disaster or not.

## Data analysis:
```
1, just happened a terrible car crash
0, self destruction mode!
0, 30 seconds for my bitches to evacuate
1, there is a forest fire at spot pond, geese are fleeing across the street, i cannot save them all
0, fire waves and darkness 
0, if she don't know bout that pandemonium album
1, apocalypse lighting. #spokane #wildfires
 ```
After some data analysis we can see that the data is quite biased. With a mean of .43 it's more leaning towards not real. 
To make matters worse we only have about *7613* samples which makes it hard not to overfit considering there are *23526* diffirent words in the dataset. After tokenization and omitting words that have a frequency less than 10 we end up with *1489* diffirent words/tokens

## Model:
```
Layer (type)                 Output Shape              Param #   
=================================================================
embedding_1 (Embedding)      (None, 15, 100)           148900    
_________________________________________________________________
bidirectional_2 (Bidirection (None, 15, 100)           60400     
_________________________________________________________________
bidirectional_3 (Bidirection (None, 100)               60400     
_________________________________________________________________
dropout_3 (Dropout)          (None, 100)               0         
_________________________________________________________________
dense_3 (Dense)              (None, 1024)              103424    
_________________________________________________________________
dropout_4 (Dropout)          (None, 1024)              0         
_________________________________________________________________
dense_4 (Dense)              (None, 128)               131200    
_________________________________________________________________
dropout_5 (Dropout)          (None, 128)               0         
_________________________________________________________________
dense_5 (Dense)              (None, 1)                 129       
=================================================================
Trainable params: 504,453
```

## Results:
Right out of the box I was able to get a test accuracy of *68%*. Not the best, but not great either considering there is a strong bias. I'm guessing that with some tweaking you could get it up to 70-75% accuracy, which is alot better!
