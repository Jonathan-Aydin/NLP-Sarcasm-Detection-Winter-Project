Sarcasm Detection in News Headlines Using BERT

Name: Jonathan Aydin
Email: gaboroaydin@gmail.com (jaydin@usc.edu)

—————————————————————————————————————————————————————————————————————

Project Overview

In this project, I developed a Natural Language Processing (NLP) model to detect sarcasm in news headlines. The model, leveraging a pre-trained BERT architecture, aims to discern sarcastic tones in textual data, a challenging aspect of language understanding.

—————————————————————————————————————————————————————————————————————

Dataset

Description and Preprocessing

We used the "News Headlines Dataset for Sarcasm Detection", sourced from TheOnion and HuffPost. The dataset contains headlines labeled as sarcastic (is_sarcastic: 1) or not (is_sarcastic: 0). To prepare the data for our model:

	•	Tokenization: Utilizing the BertTokenizer from the Hugging Face transformers library, headlines were broken down into tokens. This process converts text into a format that is compatible with the BERT model. The choice of tokenizer directly aligns with the pre-trained model's understanding of language structure.
	•	Sequence Length Standardization: Given the variability in headline lengths, each input sequence was standardized to a length of 128 tokens. This length was chosen to ensure enough contextual information while maintaining computational efficiency. Sequences shorter than 128 tokens were padded, and longer ones were truncated.
	•	Train-Test Split: The dataset was divided into a training set (85%) and a testing set (15%). This split ensured a substantial amount of data for model training while reserving an adequate portion for model evaluation.

The dataset's composition of professionally written headlines means fewer anomalies like slang or misspellings, which aligns well with BERT's training on formal text sources. Standardizing sequence length and data splitting was crucial to prepare the data for effective model training and unbiased evaluation.

—————————————————————————————————————————————————————————————————————

Model Development and Training

Implementation Choices

	•	Model: BERT (bert-base-uncased), known for its deep understanding of language nuances and context, was an obvious choice for sarcasm detection, which is inherently subtle and context-dependent.
	•	Architecture: A dense layer with a sigmoid activation function was added on top of the BERT model for binary classification. This layer interprets the representations from BERT and outputs the probability of the headline being sarcastic.

Training Procedure

	•	Optimizer: Adam, selected for its effectiveness in handling sparse gradients and its adaptive learning rate capabilities, which are beneficial for fine-tuning tasks.
	•	Learning Rate: Set to 1e-5, a lower rate to make small, incremental adjustments to the pre-trained model, reducing the risk of overfitting.
	•	Loss Function: Binary Cross-Entropy, ideal for binary classification tasks as it quantifies the difference between the predicted probabilities and the actual labels.
	•	Epochs: Limited to 3 to balance between sufficient learning and the risk of overfitting, considering BERT's sensitivity to over-training.

Hyperparameters

	•	Batch Size: 32, a recommended size for fine-tuning BERT.
	•	Maximum Sequence Length: Set to 128 tokens to capture sufficient context from each headline.


Model Evaluation/Results

Performance Metrics

	•	Accuracy: Approximately 96%. This high accuracy indicates that the model can correctly identify sarcasm in most cases.
	•	Loss: Approximately 0.0942. Observed both in training and validation. The training loss continued to decrease, while the validation loss showed slight increases, suggesting overfitting.

Results
The model achieved an accuracy of around 96.46% with a loss of 0.0942. However, there was a noticeable divergence between training and validation loss, suggesting possible overfitting.

—————————————————————————————————————————————————————————————————————


Discussion

Fit for Task

	•	Dataset: The dataset's professional writing style aligns well with BERT's pre-training on diverse and formal language sources.
	•	Model Architecture: BERT's deep understanding of language context makes it a strong fit for detecting sarcasm, which often relies on subtle language cues.

Wider Implications and Social Good

	•	Content Moderation: This model can aid in flagging sarcastic content, which is crucial in contexts like news dissemination and social media.
	•	Sentiment Analysis: An extension of this work could contribute to more nuanced sentiment analysis tools.

Limitations

	•	Context Dependence: Sarcasm often relies on external context, which may not be fully captured by the model.
	•	Data Diversity: The dataset, though high quality, is limited to two sources, which might affect the model's generalizability.

Next Steps

	•	Incorporate Context: Experiment with models that can factor in external context.
	•	Dataset Expansion: Include more diverse data sources for training.
	•	Hyperparameter Tuning: Further tuning and regularization to address overfitting.

In conclusion, this project demonstrates the feasibility of using advanced NLP models like BERT for nuanced language tasks such as sarcasm detection. While promising, the model's current limitations highlight the need for more context-aware and diverse training approaches in the field of sentiment analysis.
