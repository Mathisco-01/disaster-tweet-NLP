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
embedding_13 (Embedding)     (None, 25, 500)           1863500   
_________________________________________________________________
bidirectional_26 (Bidirectio (None, 25, 1000)          4004000   
_________________________________________________________________
bidirectional_27 (Bidirectio (None, 600)               3122400   
_________________________________________________________________
dense_44 (Dense)             (None, 1024)              615424    
_________________________________________________________________
dropout_29 (Dropout)         (None, 1024)              0         
_________________________________________________________________
dense_45 (Dense)             (None, 512)               524800    
_________________________________________________________________
dropout_30 (Dropout)         (None, 512)               0         
_________________________________________________________________
dense_46 (Dense)             (None, 128)               65664     
_________________________________________________________________
dropout_31 (Dropout)         (None, 128)               0         
_________________________________________________________________
dense_47 (Dense)             (None, 1)                 129       
=================================================================
Total params: 10,195,917
```

## Results:
Right out of the box I was able to get a test accuracy of *71%*. Not the best, but not great either considering there is a strong bias. I'm guessing that with some tweaking you could get it up to 75-90% accuracy, which is alot better!
