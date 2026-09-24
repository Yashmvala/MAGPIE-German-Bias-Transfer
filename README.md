# Zero-Shot Cross-Lingual Media Bias Detection: Applying MAGPIE to German News at the Article Level

**MSc Thesis Project**

**Author:** Yashkumar Vala  
**Programme:** MSc Data Science, AI, and Digital Business  
**University:** GISMA University of Applied Sciences  
**Supervisor:** Prof. William Baker Morrison

---

## Overview

This repository contains the code and analysis notebooks for the MSc thesis **“Zero-Shot Cross-Lingual Media Bias Detection: Applying MAGPIE to German News at the Article Level.”**

The project investigates whether **MAGPIE**, a multi-task media bias detection model trained on English data, can transfer its bias-detection ability to German news articles without German-language fine-tuning.

As MAGPIE produces sentence-level predictions, several pooling strategies are evaluated to obtain article-level scores.

---

## Research Question

> **Does MAGPIE, a multi-task bias detection model trained only on English, transfer its bias-detection ability to German news at the article level without any German-language fine-tuning?**

---

## Repository Structure

```
MAGPIE-German-Bias-Transfer/
│
├── README.md
│
├── 01_german_analysis.ipynb
│   └── Main German transfer analysis
│
├── 02_babe_analysis.ipynb
│   └── BABE pipeline sanity check
│
├── 03_semeval_analysis.ipynb
│   └── SemEval-2019 English comparison
│
├── 04_spanish_analysis.ipynb
│   └── Spanish replication analysis
│
├── 05_topic_modelling.ipynb
│   └── BERTopic and topic-controlled analysis
│
└── 06_outlet_genre_baseline.ipynb
    └── Outlet, genre, and SentiWS analysis
```
Each notebook is self-contained and includes its own data loading, model scoring, statistical analysis, and explanatory markdown.

⸻

Methodology

The analysis uses MAGPIE sentence-level predictions and aggregates them to the article level using:


* Continuous average
* Hard-label average
* Maximum
* Median
* Top-3
* Top-5

Additional analyses examine:

* Article-length effects
* Length-controlled comparisons
* Outlet-level clustering
* Cluster-robust inference
* HC3 robust standard errors
* Bonferroni correction
* Topic effects
* SentiWS-based lexical analysis

⸻

## Datasets

The project uses the following datasets and resources:

### España-Bonet (2023)
Used for the German and Spanish news analyses.

### BABE
Used as a sanity check for the MAGPIE scoring and analysis pipeline.

### SemEval-2019 Task 4
Used as an independent English comparison dataset.

### SentiWS
Used as a German sentiment lexicon baseline.

Third-party datasets are not included in this repository. They should be obtained from their original sources in accordance with their respective licenses and attribution requirements.
⸻

Key Findings

The primary German analysis does not provide reliable evidence of a general article-level left/right distinction in MAGPIE scores once article length and outlet clustering are taken into account.

The Spanish analysis provides mixed evidence.

Additional analyses suggest that MAGPIE’s German outputs may be more strongly associated with subjectivity, evaluative language, and topic composition than with outlet-level political stance alone.

For the complete statistical results and interpretation, please refer to the MSc thesis.

⸻

Requirements

The notebooks were developed and executed using Google Colab.

Main Python libraries include:

* transformers
* pandas
* numpy
* scipy
* statsmodels
* bertopic
* datasets
* sentence-transformers

⸻

How to Run

1. Clone or download this repository.
2. Open the required notebook in Google Colab.
3. Install the dependencies specified in the notebook.
4. Obtain the required third-party datasets.
5. Place the datasets in the expected locations or update the relevant paths.
6. Run the notebook sequentially.

⸻

Reproducibility

A fixed random seed of 42 was used for sampling.

The German analysis also saves a standalone CSV containing the sampled article oscarID, URL, and stance label.

The notebooks contain the relevant preprocessing and corpus-reading procedures required to reproduce the analyses.

⸻

Thesis

Title:
Zero-Shot Cross-Lingual Media Bias Detection: Applying MAGPIE to German News at the Article Level

Author: Yashkumar Vala
Programme: MSc Data Science, AI, and Digital Business
University: GISMA University of Applied Sciences
Supervisor: Prof. William Baker Morrison
