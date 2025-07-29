# Multi-Label-Text-Classification

Link to Dataset: [PubMed Multi-Label Text Classification](https://www.kaggle.com/datasets/owaiskhan9654/pubmed-multilabel-text-classification)

## Overview
First let us look at the datasets provided. There are 2 similar datasets provided - the first one, which is "PubMed Multi Label Text Classification Dataset.csv" is a smaller dataset with around 10000 samples of data. This dataset can be used to understand the structure of the data, as the file size is small enough to open with Google Docs and upload to GitHub. It has 2 extra labels compared to the processed dataset but 

"PubMed Multi Label Text Classification Dataset Processed.csv" is the dataset to be used to train a model to perform the multi-label classification task. It contains around 50000 samples of data. The structure of the dataset is as follows:

1. It contains a total of 20 colums; Title (title of the article), abstractText (an abstract version of the article), meshMajor (medical subheadings assigned to the article), pmid (PubMed Unique ID), meshid (MeSH ID), meshroot (MeSH mapped root).
2. The next 14 columns are the labels that an article can fall under. Some of the labels are A (anatomy), B (organisms), C (diseases).

An article can fall under multiple categories. So this problem cannot be considered as a usual multi class classification where only one class is predicted for one data point.
