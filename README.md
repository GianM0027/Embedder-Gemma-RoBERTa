# Embedder Gemma-RoBERTa

This repository hosts the project work for the Data Mining, Text Mining, and Big Data Analytics course. It centers on the development and evaluation of an embedding creation pipeline using a large language model (`gemma_2b_en`) attached to a small language model (`roberta-base`).

## Project Overview

We delved into the purpose and creation of embeddings, analyzing the source code of the MTEB framework to understand its functionality. Moreover, we explored the possibility of enhancing training efficiency and model performance in text classification tasks. The methodology and performance metrics are derived from the MTEB framework, with results compared against other models on the [MTEB leaderboard](https://huggingface.co/spaces/mteb/leaderboard).

### Key Features
- Utilizes `Gemma`, a large language model, to generate deep contextual embeddings.
- Adapts embeddings to fit the input requirements of the `RoBERTa` small language model through a specialized feed-forward layer.
- Evaluates model performance on standard datasets, aiming to advance the standings on the MTEB leaderboard specifically for classification tasks.

## Getting Started

Follow these steps to set up and execute the project notebooks on Kaggle.

### Prerequisites
- Access to a Kaggle account.
- An API token from Hugging Face to access model APIs, along with the permission for using `google/Gemma_2b` and `roberta-base`.

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
   - The notebook's last cell outputs performance metrics including accuracy and F1 scores.

## Results

An extensive set of experiments has been conducted on two datasets:

1. **Amazon Counterfactual Classification**: A binary classification task.
2. **Emotion Classification**: A multilabel (6 labels) classification task.

A complete description of experiments and results can be found in the `Report.pdf` file.

To reproduce these results, modify the first cell of the notebook to match the configuration parameters specified below:

| **Parameter**  | **Amazon Counterfactual Classification** | **Emotion Classification** |
| -------------- | ---------------------------------------- | -------------------------- |
| Seed           | 33                                       | 33                         |
| Epochs         | 6                                        | 5                          |
| Batch Size     | 8                                        | 32                         |
| Learning Rate  | 1.00E-05                                 | 1.00E-05                   |
