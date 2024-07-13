# Embedder Gemma-RoBERTa

This repository hosts the project work for the Data Mining, Text Mining, and Big Data Analytics course. It centers on the development and evaluation of an embedding creation pipeline using a large language model (`gemma_2b_en`) attached to a small language model (`RoBERTa base`).

## Project Overview

 We explored the possibility to enhance training efficiency and model performance in text classification tasks. The methodology and performance metrics are derived from the MTEB framework, with results compared against other models on the [MTEB leaderboard](https://huggingface.co/spaces/mteb/leaderboard).

### Key Features
- Utilizes `Gemma`, a large language model, to generate deep contextual embeddings.
- Adapts embeddings to fit the input requirements of the `RoBERTa` small language model through a specialized feed-forward layer.
- Evaluates model performance on standard datasets, aiming to advance the standings on the MTEB leaderboard specifically for classification tasks.

## Getting Started

Follow these steps to set up and execute the project notebooks on Kaggle.

### Prerequisites
- Access to a Kaggle account.
- An API token from Hugging Face to access model APIs.

### Setup Instructions

1. **Clone the Repository**
   - Clone this repository to a local machine or directly on Kaggle. Original tests were performed on Kaggle's cloud environment due to hardware constraints, hence this guide focuses on cloud execution.

2. **Import Notebook to Kaggle**
   - Upload the project notebook to your Kaggle account.

3. **Configure API Token**
   - In Kaggle:
     - Navigate to the "Add-ons" tab and select "Secrets".
     - Opt to "New Secret", name it `HUGGING_FACE_TOKEN`, and insert your Hugging Face API token as the value.

4. **Adjust Notebook Settings**
   - Ensure the Kaggle notebook is configured to use a GPU accelerator, specifically a P100 GPU.

## Usage Guide

Execute the experiments by following these steps:

1. **Parameter Configuration**
   - Modify the first cell of the notebook to adjust parameters for the test configuration, such as the number of layers from the LLM, pooling strategies, and model specifics.

2. **Run the Notebook**
   - Execute all notebook cells, ensuring each one completes successfully to validate the results.

3. **Interpret Results**
   - The notebook outputs performance metrics including accuracy and F1 scores, which are essential for assessing the effectiveness of the embedding strategies against MTEB leaderboard entries.

## Results

An extensive set of experiments has been conducted on two datasets:

1. **Amazon Counterfactual Classification**: a binary classification task.
2. **Emotion Classification**: a multilabel (6 labels) classification task.

These configurations were essential to ensure consistency and reproducibility of results across both datasets. Below are the performance metrics obtained for each model evaluated:

| **Model**           | **Amazon Counterfactual Classification (Accuracy, F1)** | **Emotion Classification (Accuracy, F1)** | **Layer Number** |
|---------------------|---------------------------------------------------------|-------------------------------------------|------------------|
| Roberta-Only        | (0.92358, 0.88786)                                      | (0.84130, 0.79769)                        | -                |
| Gemma-Only          | (0.65224, 0.59531)                                      | (0.28535, 0.24303)                        | -                |
| Full Model [1-18]   | (0.59567, 0.53944)                                      | (0.32005, 0.20509)                        | -1               |
| Model [1-17]        | (0.73567, 0.67447)                                      | (0.29070, 0.23099)                        | -2               |
| Model [1-16]        | (0.78910, 0.73468)                                      | (0.33010, 0.25578)                        | -3               |
| Model [1-15]        | (0.81881, 0.75857)                                      | (0.33950, 0.27807)                        | -4               |
| Model [1-14]        | (0.83522, 0.77633)                                      | (0.17060, 0.11551)                        | -5               |
| Model [1-13]        | (0.82284, 0.76580)                                      | (0.35050, 0.28033)                        | -6               |
| Model [1-12]        | (0.84746, 0.79004)                                      | (0.21150, 0.12383)                        | -7               |
| Model [1-11]        | (0.73687, 0.66874)                                      | (0.21770, 0.17535)                        | -8               |
| Model [1-10]        | (0.85896, 0.80996)                                      | (0.35980, 0.28138)                        | -9               |
| Model [1-9]         | (0.82060, 0.76040)                                      | (0.33605, 0.26878)                        | -10              |
| Model [1-8]         | (0.77179, 0.72740)                                      | (0.29690, 0.24354)                        | -11              |
| Model [1-7]         | (0.78119, 0.71965)                                      | (0.39920, 0.32163)                        | -12              |
| Model [1-6]         | (0.80448, 0.75166)                                      | (0.24650, 0.19516)                        | -13              |
| Model [1-5]         | (0.85119, 0.79530)                                      | (0.39890, 0.32221)                        | -14              |
| Model [1-4]         | (0.87493, 0.82954)                                      | (0.18935, 0.14127)                        | -15              |
| Model [1-3]         | (0.82194, 0.76370)                                      | (0.19300, 0.13079)                        | -16              |
| Model [1-2]         | (0.77567, 0.71621)                                      | (0.18550, 0.14802)                        | -17              |
| Model [1]           | (0.65090, 0.58423)                                      | (0.32005, 0.20508)                        | -18              |

In this table, the 'Layer Number' column specifies from which layer the output of Gemma is being extracted. Negative numbers indicate the layer count starting from the topmost layer downward. The rows labeled 'Roberta-Only' and 'Gemma-Only' serve as baseline comparisons, demonstrating the performance of the standalone models without integration.

To reproduce these results, modify the first cell of the notebook to match the configuration parameters specified below:

| **Parameter**  | **Amazon Counterfactual Classification** | **Emotion Classification** |
| -------------- | ---------------------------------------- | -------------------------- |
| Seed           | 33                                       | 33                         |
| Epochs         | 6                                        | 5                          |
| Batch Size     | 8                                        | 32                         |
| Learning Rate  | 1.00E-05                                 | 1.00E-05                   |

