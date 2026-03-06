# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MIT MBA course 15.773 group project. The goal is fake news detection using NLP/Transformer models, applied to the [Kaggle fake-and-real-news dataset](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset) (~44,898 articles).

## Running Notebooks

Open and run notebooks with Jupyter:
```bash
jupyter notebook
```

Or run a single notebook non-interactively:
```bash
jupyter nbconvert --to notebook --execute EDA.ipynb
```

## Architecture

### EDA.ipynb
The main data pipeline notebook:
1. Downloads dataset via `kagglehub` (`clmentbisaillon/fake-and-real-news-dataset`) — produces `True.csv` and `Fake.csv`
2. Labels true news as `truth=1`, fake as `truth=0`, concatenates into `combined_df` (44,898 rows, columns: `title`, `text`, `subject`, `date`, `truth`)
3. Shuffles and reduces to `master` df with only `text` and `truth` columns
4. 70/30 train/test split via `sklearn.train_test_split` with `random_state=42` → `train` (31,428 rows), `test` (13,470 rows)

Kaggle credentials are set via environment variables (`KAGGLE_USERNAME`, `KAGGLE_KEY`) at the top of the notebook.

### BERT_model_example.ipynb
A reference/template notebook (not directly part of the fake-news task) demonstrating RoBERTa fine-tuning on song lyrics genre classification using `keras_hub`. Use this as the modeling pattern for applying transformers to the fake news task.

Key pattern from the example:
- Load `keras_hub.models.RobertaClassifier.from_preset("roberta_base_en", num_classes=N)`
- Compile with `Adam(1e-5)` and `SparseCategoricalCrossentropy(from_logits=True)`
- Pass raw text strings directly to `classifier.fit()` — the preprocessor tokenizes automatically

## Dependencies

```
kagglehub, pandas, numpy, scikit-learn, keras, keras-hub, tensorflow
```
