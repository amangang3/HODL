# HODL — Fake News Detection
**MIT MBA 15.773 Group Project**

This repository contains the code and models for our HODL group project: detecting fake news using NLP and transformer-based models, applied to a dataset of ~44,898 news articles.

---

## Project Overview

We train and evaluate multiple models to classify news articles as real or fake:

- **BERT.ipynb** — Fine-tuned BERT/RoBERTa transformer model for fake news classification
- **BoW Model.ipynb** — Bag-of-Words baseline model for comparison

The dataset is the [Kaggle Fake and Real News Dataset](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset), downloaded automatically via `kagglehub`.

---

## Setup & Requirements

Install dependencies:
```bash
pip install kagglehub pandas numpy scikit-learn keras keras-hub tensorflow openpyxl
```

Set your Kaggle API credentials as environment variables before running the notebooks:
```bash
export KAGGLE_USERNAME=your_username
export KAGGLE_KEY=your_api_key
```

---

## Custom Data (Required)

Several notebooks use manually curated datasets that must be present in the root of the repository:

| File | Description |
|------|-------------|
| `custom test dataset.xlsx` | Custom test articles for model evaluation |
| `synthetic_fake_news_combined.xlsx` | Synthetically generated fake news articles used in training |

These files are included in the repo. If you clone this repository, they will be available automatically.

---

## Running the Notebooks

Open Jupyter and run the notebooks in order:

```bash
jupyter notebook
```

Or run non-interactively:
```bash
jupyter nbconvert --to notebook --execute BERT.ipynb
jupyter nbconvert --to notebook --execute "BoW Model.ipynb"
```

---

## Team

HODL Group — MIT MBA 15.773
