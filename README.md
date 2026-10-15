# BERT Masked Language Model Demo

A small step-by-step notebook showing how BERT fills in a blank word.

![BERT masked language model](/bert_mlm.png)

```
Input : I sat by the river [MASK] to enjoy the view.
Output: I sat by the river bank to enjoy the view.
```

## How it works

BERT reads the whole sentence at once. For the `[MASK]` token it looks at the words on both sides ("river", "to enjoy the view") and predicts the most likely word.

1. Tokenize the sentence, with `[CLS]` and `[SEP]` added automatically.
2. Replace the target word with `[MASK]`.
3. Run `BertForMaskedLM` to get a score for every word in the vocabulary.
4. Take the top predictions at the `[MASK]` position and fill the blank.

## Requirements

- Python 3.10+
- `transformers`
- `torch`

```bash
pip install transformers torch
```

## Usage

1. Open `bert.ipynb`.
2. Run the cells from top to bottom.
3. The last cell prints the input sentence and the sentence with the blank filled in.

The model is `bert-base-cased` (about 110M parameters). It runs fine on CPU, so no GPU is needed. The first run downloads the weights.


## Reference

Code follows the GeeksforGeeks BERT tutorial.
