# SKIMLIT

In this project, we're going to be replicating the deep learning model behind the 2017 paper <a href = 'https://arxiv.org/abs/1710.06071'>PubMed 200k RCT:</a> a Dataset for Sequenctial Sentence Classification in Medical Abstracts.
And reading through the paper above, we see that the model architecture that they use to acheive their best results is available here: <a href = 'https://arxiv.org/abs/1612.05251'> Neural Networks for Joint Sentence Classification in Medical Paper Abstracts.

When it was released, the paper presented a new dataset called PubMed 200k RCT which consists of ~200,000 labelled Randomized Controlled Trial (RCT) abstracts.

The goal of the dataset was to explore the ability for NLP models to classify sentences which appear in sequential order.

## Creating a series of model experiments

After proprocessing our data, in true machine learning fashion, it's time to setup a series of modelling experiments.

We'll start by creating a simple baseline model to obtain a score we'll try to beat by building more and more complex models as we move towards replicating the sequence model outlined in Neural networks for joint sentence classification in medical paper abstracts.

For each model, we'll train it on the training data and evaluate it on the validation data.
```
Model 1: Conv1D with token embeddings
```
```
Model 2: TensorFlow Hub Pretrained Feature Extractor
```
* <a href = 'https://tfhub.dev/google/universal-sentence-encoder/4'>TensorFlow Hub Pretrained Feature Extractor</a>
* The paper originally used GloVe embeddings, however, we're going to stick with the later create USE pretrained embeddings.
```
Model 3: Model 3: Conv1D with character embeddings
```
* The paper which we're replicating statest they used a combination of token and character-level embeddings.
```
Model 4: Combining pretrained token embeddings + character embeddings (hybrid embedding layer)
```
* Using tf.concatenate function to combine token and character-level embeddings and produces sequence label probabilites as output.
```
> Model 5: Transfer learning with pretrained token embeddings + character embeddings + positional embeddings
```

### Prerequisites

```
Dataset: https://github.com/Franck-Dernoncourt/pubmed-rct
Command: !git clone https://github.com/Franck-Dernoncourt/pubmed-rct
```

```
Requirements: pip install -r requirements.txt
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
