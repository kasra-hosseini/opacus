# Overview

This example demonstrates how to run a privacy-preserving LSTM (with DP) on a name classification task. This is the same task as in this old PyTorch tutorial https://pytorch.org/tutorials/intermediate/char_rnn_classification_tutorial.html, with a rewrite that aligns its style to modern PyTorch.

# Sample run

Download the training zip from https://download.pytorch.org/tutorial/data.zip and then extract it to a local directory. In this example, we assume that the data path is /home/data_folder/names/*.txt

Run with dp:

```
python char-lstm-classification.py --epochs=50 --learning-rate=2.0 --hidden-size=128 --delta=8e-5 --batch-size=800 --n-lstm-layers=1 --sigma=1.0 --max-per-sample-grad-norm=1.5 --device=cuda:0 --data-root="/my/folder/data/names/" --test-every 5
```

You should get something like this: Test Accuracy: 0.732173 (ε = 14.11, δ = 1e-06) for α = 3.0

Run without dp:

```
python char-lstm-classification.py --epochs=50 --learning-rate=0.5 --hidden-size=128 --batch-size=800 --n-lstm-layers=1 --disable-dp --device=cuda:1 --data-root="/my/folder/data/names/" --test-every 5
```
You should get something like this: Test Accuracy: 0.756958
