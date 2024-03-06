# Aspect-Based-Sentiment-Analysis
Aspect-Based Sentiment Analysis (ABSA) on the Multi-Aspect Multi-Sentiment (MAMS) dataset



## Introduction
For extracting, analyzing, and understanding aspects, features, and sentiments from textual data. This script aims to derive meaningful insights from texts such as customer reviews. 

## Extracting and Mapping Aspects
The `extract_and_map_aspects` function's objective is to detect key aspects within the text and align them with a predefined set of aspect labels. Here's the breakdown of tools used:

### spaCy
- **Tool**: [spaCy](https://spacy.io/)
- **Purpose**: Text processing for tokenization and named entity recognition.
- **Reason**: Known for its efficiency, low recourse and accuracy, spaCy is utilized to decompose the input text into noun chunks, serving as potential aspects.

### Sentence Transformers
- **Tool**: [MiniLM embeddings](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)
- **Purpose**: Mapping extracted aspects to predefined labels.
- **Reason**: Chosen for its ability to semantically match the text's aspects with predefined labels. These models, fine-tuned versions of BERT-like models, produce embeddings that we compare using cosine similarity to find the closest aspect label.

### Limitation to 4 Aspects
To keep the analysis focused and manageable, we cap the number of aspects to four. This pragmatic approach ensures that our analysis stays relevant to the most significant aspects mentioned in the text.

## Extracting Features/Opinions
Following the mapping, the `extract_features` function steps in with the task of pinpointing descriptive features or opinions related to each aspect. The reasons behind our approach:

### Direct Usage of spaCy
Again, spaCy's linguistic prowess is leveraged, this time to analyze the sentence's dependency tree to identify adjectives linked to the aspects, creating a direct dependency to aspects, thus extracting relevant features or opinions.

### Real Aspects for Precision
Feature extraction is based on the actual text (real aspects) to ensure accuracy. This strategy is vital for capturing the nuances and context surrounding each mentioned aspect.

## Analyzing Sentiment
The `analyze_sentiment` function assesses the sentiment on the basis of the extracted features/opinions. For sentiment analysis, a pre-trained model from Hugging Face's Transformers library is used.
