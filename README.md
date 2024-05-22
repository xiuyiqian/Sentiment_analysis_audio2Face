# Sentiment Analysis with Audio2Face

## Overview

This project aims to perform sentiment analysis using a combination of traditional LSTM networks and DistillBERT for efficient language understanding. The analysis is based on Twitter data, which is cleaned and prepared using the `Twitter_Emotion_Data_Cleaning.ipynb` notebook.

## Data Preparation

### Steps to Create the Ideal Database:

1. **Load and Inspect Data**:
   - Load raw Twitter data.
   - Inspect for inconsistencies, missing values, and irrelevant information.

2. **Data Cleaning**:
   - Remove duplicates and irrelevant entries.
   - Handle missing values appropriately.
   - Normalize text (e.g., convert to lowercase, remove punctuation).

3. **Label Encoding**:
   - Ensure emotion labels are properly encoded.

4. **Splitting Data**:
   - Split cleaned data into training, validation, and test sets.

5. **Save Cleaned Data**:
   - Save the processed dataset for modeling.

## LSTM Modeling

The LSTM model for sentiment analysis consists of the following layers:

1. **Embedding Layer**:
   - Input: Integer-encoded text sequences.
   - Embedding Matrix: Pre-trained on a large dataset.
   - Note: The embedding layer is not trainable.
   - Input Length: Set to the length of the input sequences.

2. **Bidirectional LSTM Layers**:
   - Three layers in total.
   - Each layer has a forward and backward LSTM.
   - **Dropout**: Specifies the dropout rate for inputs.
   - **Recurrent Dropout**: Specifies the dropout rate for recurrent inputs.
   - **Return Sequences**: Set to true to return the full sequences of outputs, not just the last output of each sequence.

3. **Dense Layer**:
   - Output: Linear transformation of the input.
   - Units: 6 (corresponding to the 6 emotion classes).
   - Activation: `softmax` to output a probability distribution over the 6 classes.

## DistillBERT Modeling

DistillBERT is used as a lighter, faster alternative to BERT with the following characteristics:

1. **Model Size**: DistillBERT has 40% fewer parameters than BERT while maintaining 97% of its language understanding capabilities.
2. **Performance**: Despite its reduced size, DistillBERT performs competitively on various NLP tasks.
3. **Efficiency**: It is more efficient and faster, making it suitable for applications with limited computational resources.

### Key Metrics:

- **Accuracy Score**: 0.8629751290473956
- **Macro-Averaged Precision Score**: 0.8722899934191831
- **Micro-Averaged Recall Score**: 0.8629751290473956
- **Weighted F1 Score**: 0.8633345834459296
