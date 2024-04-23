# Evidence Detection with BiLSTM

This repository contains code for training and evaluating a Bi-directional Long Short-Term Memory (BiLSTM) model for evidence detection. The code is structured to allow hyperparameter tuning, model training, validation, and prediction on test data. It also includes code to evaluate the model's performance with various metrics, such as accuracy and F1-score.

## Project Overview
The project aims to train a BiLSTM model to detect evidence in claims using tokenized and padded sequences. It uses pre-trained GloVe embeddings for initialization and applies hyperparameter tuning with Keras Tuner's `RandomSearch` to find the optimal model configuration.

## Instructions for Running the Code
   - Ensure you have the following libraries installed: `pandas`, `numpy`, `keras_tuner`, `tensorflow`, `sklearn`, and `matplotlib`.
   - Install them via `pip install <library_name>`.
   - Load GloVe embeddings to `./GloVe/glove.6B.100d.txt`.
   - Predictions are saved to `predictions.csv`


## Attribution and Data Sources
- **GloVe Embeddings**: This model is uses pre-trained GloVe embeddings found in `./GloVe/glove.6b.100d.txt`.
- **Model Storage**: The best model is saved locally to `best_model.h5`.

## Notes and Known Issues
- **Input Sequence Length**: The code uses predefined input sequence lengths for claims and evidence. Adjust these values based on the dataset to avoid truncation or excessive padding.
- **Hyperparameter Tuning**: The code uses `RandomSearch` to tune hyperparameters. The number of trials and execution settings may need adjustment based on computational resources.
- **Model Performance**: The accuracy and other metrics obtained during evaluation depend on the dataset and hyperparameters. You may need to fine-tune the model for optimal results.
