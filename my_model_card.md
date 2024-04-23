---
{}
---
language: en
license: cc-by-4.0



tags:
- text-classification
- evidence-detection

---

# Model Card for b64065ab-c62354yt-ED

<!-- Provide a quick summary of what the model is/does. -->

This is a binary classification model used for an evidence detection task. This model is based on the BiLSTM architecture.


## Model Details

### Model Description

<!-- Provide a longer summary of what this model is. -->

This model is based upon a BiLSTM architecture that was trained on 23,000 labelled training examples. 

- **Developed by:** Anandajyothis Binu and Yi Jun Tew
- **Language(s):** English
- **Model type:** Supervised
- **Model architecture:** BiLSTM

## Training Details

### Training Data

<!-- This is a short stub of information on the training data that was used, and documentation related to data pre-processing or additional filtering (if applicable). -->

23K labelled datapoints for this task was provided for training.

### Training Procedure

<!-- This relates heavily to the Technical Specifications. Content here should link to that section when it is relevant to the training procedure. -->
The preprocessing step involves tokenising both claim and evidence sequences. The sequences then padded/truncated to fit a specified length. This length was 13 for claim sequences and 65 for evidence sequences. These values were chosen because the 95th percentile claim and evidence legnths are below these values. 


#### Training Hyperparameters

<!-- This is a summary of the values of hyperparameters used in training the model. -->

      - batch_size: 16
      - num_epochs: 4
      - num_bilstm_layers: 3  
      - dropout_0: 0.2
      - droupout_1: 0.0
      - droupout_2: 0.0
      - lstm_units_0: 64  
      - lstm_units_1: 32
      - lstm_units_2: 32
      - num_dense_layers: 1 
      - dense_units_0: 32 
      - dense_dropout_0: 0.4 
      - learning_rate: 1e-3


#### Speeds, Sizes, Times

<!-- This section provides information about how roughly how long it takes to train the model and the size of the resulting model. -->

      - overall training time: 15-40 minutes
      - duration per training epoch: 3-10 minutes
      - model size: 16.5MB

## Evaluation

<!-- This section describes the evaluation protocols and provides the results. -->

### Testing Data & Metrics

#### Testing Data

<!-- This should describe any evaluation data used (e.g., the development/validation set provided). -->

A subset of the development set provided, accounting for 6K datapoints, were used as the validation set.

#### Metrics

<!-- These are the evaluation metrics being used. -->
      - Accuracy
      - Precision
      - Recall
      - F1-score

### Results

The model obtained an F1-score of 83% and an accuracy of 83%.

Precision: 82%
Recal: 83%

## Technical Specifications

### Hardware

      - RAM: at least 4 GB
      - Storage: at least 100MB
      - GPU: optional

### Software
      - TensorFlow 2.15.0
      - keras_tuner 1.4.7

## Bias, Risks, and Limitations

<!-- This section is meant to convey both technical and sociotechnical limitations. -->

All claim sequences are truncated after 13 tokens and padded to fit this dimension. A 65 token limit is applied to the evidence sequences. These values were chosen to accomodate for the 95th percentile of sequence lengths. Any tokens after these truncation limits will not be considered by the model.

## Additional Information

<!-- Any other information that would be useful for other people to know. -->

The hyperparameters were trained using keras_tuner. Keras Tuner searched the given hyperparameter space using the hyperband strategy. This helped prune seemingly suboptimal values for hyperparameters. The evaluation metric used was classification accuracy on the validation set.
