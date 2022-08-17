# Training a transformer
There is three main steps when training a Transformer:
- Training of the Tokenizer
- Pretraining, also called language modeling
- Fine tuning, which consist in adding an extra layer on top of the pretrained model for a downstream task

# What to do depending on your use case

If text similar to training text
- Directly fine tune on downstream task

If text not that similar (for example model trained on wikipedia but you want to work on tweet)
- Fine tune language modelling

If text not similar but same language
- Retrain language modelling from scratch

If text nothing similar (new language, programming language, etc…)
- Retrain all from scratch( tokenizer and model)

For fine tuning, if you feel only training the last layer won't be enough because text particularities, you can freeze bottom layer and only train some top layers. See below for more informations:
https://discuss.huggingface.co/t/what-is-transfer-learning-and-why-is-it-needed/4431
https://discuss.huggingface.co/t/how-to-freeze-some-layers-of-bertmodel/917
https://discuss.huggingface.co/t/gradual-layer-freezing/3381/2

For example, if you have limited hardware, it can be interesting to freeze half the layers for pretraining and then freeze all the layers for your downstream task training.
