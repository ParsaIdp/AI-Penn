# Protein Function Prediction Using DistilProtBERT & DistilBioBERT

This repository implements a protein function prediction pipeline based on the CAFA-5 Protein Function Prediction challenge. It leverages the pre-trained models **DistilProtBERT** (for protein sequence encoding) and **DistilBioBERT** (for GO term encoding) along with LoRA fine-tuning to predict the association between protein sequences and gene ontology (GO) functions.

## Overview

The code in this repository performs the following tasks:
- **Data Download & Extraction:** Downloads the CAFA-5 dataset from Kaggle and unzips the necessary files.
- **Data Preprocessing:** Processes protein sequences and GO term mappings from the provided files.
- **Dataset Preparation:** Constructs a custom PyTorch dataset that pairs protein sequences with their corresponding GO term descriptions.
- **Model Architecture:** Defines a `ProteinPredictor` model which:
  - Uses DistilProtBERT to extract protein embeddings.
  - Uses DistilBioBERT to extract GO term embeddings.
  - Combines these embeddings and passes them through an MLP for binary classification.
- **LoRA Fine-Tuning:** Applies a LoRA configuration via the PEFT library to fine-tune select layers efficiently.
- **Training & Evaluation:** Trains the model and evaluates its performance using metrics such as ROC curves, recall, precision, and F1-score.
- **Interactive Prediction (Optional):** Provides an interactive UI (using ipywidgets) to enter a protein sequence and display predicted GO term confidence scores with visualizations.

## Requirements

- Python 3.7 or later
- [Kaggle API](https://github.com/Kaggle/kaggle-api)
- PyTorch
- Transformers
- obonet
- Biopython
- PEFT
- scikit-learn
- tqdm
- matplotlib
- ipywidgets (for interactive prediction)

## Setup Instructions

1. **Kaggle Credentials:**

   Update the following lines in your notebook with your Kaggle credentials:
   ```python
   os.environ["KAGGLE_USERNAME"] = "YOUR_KAGGLE_USERNAME"
   os.environ["KAGGLE_KEY"] = "YOUR_KAGGLE_KEY"
