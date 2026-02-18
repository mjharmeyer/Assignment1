# README — Sentiment Classification Program

## Project Overview

This project implements and evaluates three classification models to predict the sentiment of short text sentences:

* Custom K-Nearest Neighbors (KNN)
* Naïve Bayes
* Decision Tree

The program compares classifier performance using two feature representations:

* **FV-1**: Full bag-of-words representation
* **FV-2**: Top-1024 selected features with stop-word removal

Each model is evaluated using multiple performance metrics and computational cost measurements. ROC curves are also generated to visualize classifier behavior.

The goal of this project is to examine how feature selection affects prediction quality and efficiency.

---

## Directory Structure

```
project_folder/
│
├── 5243assignment1.py      # Main Python script
├── merged_dataset.txt      # Sentiment dataset (required input)
└── README.md               # Documentation
```

### Dataset File

`merged_dataset.txt` must:

* be tab-separated
* contain two columns:

  * sentence text
  * binary sentiment label (0 = negative, 1 = positive)

Example:

```
This movie was great	1
I did not like this product	0
```

---

## Required Packages

Install the following Python libraries before running the program:

```
pandas
numpy
nltk
matplotlib
scikit-learn
```

### Install with pip

```
pip install pandas numpy nltk matplotlib scikit-learn
```

The program will automatically download required NLTK tokenization resources during execution.

---

## How to Run the Program

1. Place `merged_dataset.txt` in the same directory as the script.
2. Open a terminal in the project folder.
3. Run:

```
python 5243assignment1.py
```

The script will:

* preprocess text
* generate feature matrices
* split data into training, validation, and test sets
* train classifiers
* evaluate performance
* display ROC plots

---

## Program Workflow

### 1. Text Preprocessing

* Converts text to lowercase
* Tokenizes sentences
* Applies stemming using Porter Stemmer
* Removes non-alphanumeric tokens

### 2. Feature Generation

FV-1:

* Full bag-of-words representation

FV-2:

* Top 1024 features
* Common stop words removed

### 3. Data Splitting

Dataset is split into:

* 60% training
* 20% validation
* 20% test

### 4. Model Training

Three classifiers are trained:

* Custom KNN (Euclidean distance)
* Multinomial Naïve Bayes
* Decision Tree

### 5. Evaluation Metrics

Each model reports:

* Accuracy — overall prediction correctness
* Precision — proportion of correct positive predictions
* Recall — ability to detect positive cases
* Specificity — ability to detect negative cases
* AUROC — classification separability
* Offline Cost — training time
* Online Cost — prediction time

---

## Understanding the Output

After execution, a performance table is printed:

```
Accuracy  Precision  Recall  Specificity  AUROC  Offline Cost  Online Cost
```

Interpretation:

* Higher Accuracy / Precision / Recall → better classification
* Higher AUROC → stronger class separation
* Lower Offline Cost → faster training
* Lower Online Cost → faster prediction

You can compare FV-1 vs FV-2 to understand the effect of feature selection.

---

## ROC Curve Visualization

Two ROC plots are generated:

* ROC for full feature representation
* ROC for reduced feature representation

Curves closer to the top-left corner indicate better classifier performance.

---

## Assumptions

* Sentiment is binary (positive or negative)
* Dataset samples are representative
* Text preprocessing preserves meaningful structure
* Feature frequency approximates importance

---

## Notes

* Custom KNN is implemented for educational purposes and may be slower than optimized libraries.
* Feature selection improves efficiency for distance-based classifiers.
* Random seeds ensure consistent dataset splits.
