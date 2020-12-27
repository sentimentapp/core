# BERT Style Transformer for Emotion Classification in Text

Check out a working demo of the model at https://colab.research.google.com/drive/1bpvIRcNmKAKpKD1ZM3J7BPyiJtFysF1i#scrollTo=be_nF9XOxSFr.
<br>
<br>
See how the model was integrated into the Sentiment app at https://github.com/sentimentapp/application/tree/feature.transformer/src/modules/model.

<br>

## Description
The model contained within this folder is primarily based off of the open source [BERT Transformer created Google AI](https://ai.googleblog.com/2018/11/open-sourcing-bert-state-of-art-pre.html). Unlike the previous [CNN-LSTM](https://github.com/sentimentapp/core/tree/main/cnn-lstm) created for this project which used dimensional classification (*e.g.,* valance is 3.15 and dominance is -1.24), this model classifies text entries with discrete emotions (labeling them happy, sad, etc...). This model originally intended to use the same dimensional Emobank dataset used by the CNN-LSTM, but after examining the training of both the Transformer and LSTM, it was concluded that the text data didn't have a strong correlation with its labels.
The Transformer model is also much smaller, taking up only 2.6 MB due to the fact that it includes its own word vectors rather than pretrained ones. 

## Issues
However, it is important to note the numerous shortcomings of this model. While this model is small, most of the models shrinkage can be credited to the to lack of correlation in the discrete emotion datasets used for training. After attempting various tweaks to the transformer model, **a test accuracy of only 46%** was able to be obtained. While this is a step up from the default 14% accuracy the model has before training, it is a left than perfect result. As stated earlier, the main issue with the training of this model appears to be the dataset used, rather than the model itself. In order to rememdy this, the model could switch to being a binary classifier of positive and negative sentiment rather than specific emotions. However while this could be used within the Sentiment app, it would remove some of functionality that is core to the concept.
