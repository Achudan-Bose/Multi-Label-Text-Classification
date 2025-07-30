# Multi-Label-Text-Classification of PubMed Articles

Link to Dataset: [PubMed Multi-Label Text Classification](https://www.kaggle.com/datasets/owaiskhan9654/pubmed-multilabel-text-classification)

## Problem Overview
First let us look at the datasets provided. There are 2 similar datasets provided. The first one is "PubMed Multi Label Text Classification Dataset.csv", a smaller dataset with around 10000 samples of data. This dataset can be used to understand the structure of the data, as the file size is small enough to open with Google Docs and upload to GitHub (available in this repository). It has 2 extra labels compared to the processed dataset, but one column (V) has all values as 0, and another column (K) has only 2 instances where the value is 1.

"PubMed Multi Label Text Classification Dataset Processed.csv" is the dataset to be used to train a model to perform the multi-label classification task. It contains around 50000 samples of data. The structure of the dataset is as follows:
1. It contains a total of 20 columns; Title (title of the article), abstractText (an abstract version of the article), meshMajor (medical subheadings assigned to the article), pmid (PubMed Unique ID), meshid (MeSH ID), meshroot (MeSH mapped root).
2. The next 14 columns are the labels that an article can fall under. Some of the labels are A (anatomy), B (organisms), C (diseases). Initially, the number of MeSH labels were so large that they had to be processed and mapped to its root label (with the help of MeSH ID) which are these 14 labels.

An article can fall under multiple categories. So this problem cannot be considered as a usual multi class classification where only one class is predicted for one data point.

## Approach
The approach was to use a pretrained SLM (Small Language Model) as a multilabel classifier. The model chosen for this purpose was BioClinical-ModernBERT-base. It builds on ModernBERT to adapt to domain-specific data. It is trained on the largest biomedical and clinical corpus to date, with over 53.5 billion tokens. It incorporates long-context processing (upto 8192 tokens) and has a significant increase in performance for bioclinical NLP tasks.

The idea was to create a pipeline consisting of separate Jupyter notebooks for each major step in training the model. This means one notebook for preprocessing, one for training and one for evaluation.
I used Google Colab to utilize the T4 GPU it provides for training. It also makes it easier to link to Google Drive, so that outputs from each notebook can be saved and used by other notebooks seamlessly.

### Preprocessing
Some additional preprocessing was required such as deleting duplicate rows and removing articles with no labels. The dataset was split into train and test data in an 80:20 split. A new column was created (in both training and test data) which was the one hot encoded values of the 14 labels as a single list. This was going to be the column to be predicted. abstractText is tokenized, then input IDs, labels and attention masks are split into train and validation data in an 80:20 split. input IDs, labels and attention masks are stored as pytorch tensors in a tensor dataset. The 3 tensor datasets (train, validation, test) are saved in Google Drive to be used by the training and validation notebooks.

### Training



