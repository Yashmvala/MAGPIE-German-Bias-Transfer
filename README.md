# Cross-Lingual Transfer of Media Bias Detection: Testing MAGPIE on German News

MSc thesis project by Yashkumar Vala, MSc Data Science, AI, and Digital Business, GISMA University of Applied Sciences.
Supervisor: Prof. William Baker Morrison.

## Overview

MAGPIE is a bias detection model that was trained only on English data. This project tests whether it can still detect bias in German news, at the article level, without ever being trained on German (this is called zero-shot cross-lingual transfer).

MAGPIE only gives a prediction for each sentence on its own. But the datasets used here only have labels at the article level (or outlet level), not per sentence. So this project also tests two ways of turning many sentence scores into one article-level score: average pooling and max pooling. Both come from the Multiple Instance Learning literature.

## Datasets

- **German (target dataset):** a sample from the corpus introduced by España-Bonet (2023), German news articles labelled left or right by the outlet's known political lean.
- **BABE (comparison, English):** the dataset MAGPIE was fine-tuned on. Used as a sanity check on the pipeline, not as independent evidence.
- **SemEval-2019 Task 4, Hyperpartisan News Detection (comparison, English):** human-annotated hyperpartisan or not labels, confirmed to not be part of MAGPIE's training data. Used as an independent English benchmark.

## Repository structure

```
notebooks/       Analysis notebooks (German, BABE, SemEval — one per dataset)
data/             (not included, see Data Availability below)
results/          Output tables and statistics from each notebook
```

## Method summary

For each dataset: articles were split into sentences, scored with MAGPIE, and aggregated to the article level using average and max pooling. Groups (e.g. left vs right) were then compared using the Mann-Whitney U test. Article length was checked throughout as a possible confound, using correlation, OLS regression, and a length-matched subsample, with Bonferroni correction applied where multiple tests were run on the same data.

## Data availability

The España-Bonet (2023) and BABE datasets are third-party research datasets and are not included in this repository. See the original papers for access. The SemEval-2019 Task 4 dataset is available via Zenodo (record 5776081).

## Reproducibility

All experiments were run in Google Colab on a T4 GPU. Main packages used: transformers, pandas, scipy, statsmodels. A fixed random seed (42) was used for the German sample so the results can be reproduced.
