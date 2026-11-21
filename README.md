# BERT Contextual Embeddings and Sentence Similarity

## Project Overview

This project explores the application of **BERT (Bidirectional Encoder Representations from Transformers)** in Natural Language Processing (NLP). It demonstrates how BERT generates contextual word embeddings and measures semantic similarity between sentences using cosine similarity.

Unlike traditional NLP techniques that rely mainly on word frequency or static representations, BERT considers the surrounding context when generating word representations. This allows it to capture different meanings of the same word depending on how it is used.

## Objectives

- Load and use a pre-trained BERT model.
- Extract contextual token embeddings.
- Demonstrate polysemy using the word *bank* in different contexts.
- Generate sentence embeddings using mean pooling.
- Calculate cosine similarity between sentence pairs.
- Classify sentence pairs using a similarity threshold of 0.7.
- Evaluate classification performance using accuracy and a confusion matrix.

## Technologies Used

- Python
- PyTorch
- Hugging Face Transformers
- BERT (`bert-base-uncased`)
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Jupyter Notebook

## Project Structure

```text
bert-contextual-embeddings-similarity/
│
├── notebooks/
│   └── bert_sentence_similarity.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

## Methodology

### 1. Loading the Pre-trained BERT Model

The `bert-base-uncased` model was loaded using Hugging Face Transformers. Its tokenizer converts sentences into token IDs, while the model generates contextual embeddings.

### 2. Tokenization

Sentences were converted into tokens and numerical representations that BERT can process.

### 3. Extracting Contextual Embeddings

BERT generated a 768-dimensional embedding for each token. These representations capture information from the surrounding context.

### 4. Demonstrating Polysemy

The word *bank* was examined in two different contexts:

- Financial context: "She deposited money at the bank."
- Geographical context: "They sat on the bank of the river."

Cosine similarity was calculated between the two contextual embeddings to demonstrate how BERT represents the same word differently depending on its meaning.

### 5. Generating Sentence Embeddings

Mean pooling was applied to the token embeddings to produce one 768-dimensional representation for each sentence. Special tokens and padding were excluded from the pooling operation.

### 6. Sentence Similarity Classification

Cosine similarity was calculated for ten sentence pairs, consisting of five original pairs and five additional pairs.

A threshold of 0.7 was applied:

- Similarity > 0.7: Classified as similar (1).
- Similarity ≤ 0.7: Classified as not similar (0).

### 7. Model Evaluation

The predicted labels were compared with manually assigned ground-truth labels. Accuracy and a confusion matrix were used to evaluate the results.

## Results

The model achieved an accuracy of **80%** on the ten sentence pairs.

| Evaluation Metric | Result |
|---|---:|
| Total sentence pairs | 10 |
| Correct predictions | 8 |
| Incorrect predictions | 2 |
| Accuracy | 80% |

### Confusion Matrix Results

| Classification | Count |
|---|---:|
| True Positives | 5 |
| True Negatives | 3 |
| False Positives | 0 |
| False Negatives | 2 |

The results show that the model correctly classified eight out of ten sentence pairs. Two semantically similar pairs were incorrectly classified as dissimilar.

## BERT vs Traditional NLP

| Feature | Traditional NLP | BERT |
|---|---|---|
| Word representation | Frequency-based or static | Contextual |
| Context understanding | Limited | Bidirectional context |
| Polysemy handling | Limited | Better contextual representation |
| Architecture | Statistical methods | Transformer |
| Semantic understanding | Limited | More advanced |

## Limitations and Recommendations

### Limitations

1. **Small Dataset:** Only ten sentence pairs were used, limiting the scope of evaluation.
2. **Fixed Similarity Threshold:** The 0.7 threshold may not be suitable for every sentence pair.
3. **Model Limitations:** BERT may not always capture subtle semantic relationships accurately.
4. **Mean Pooling:** Averaging token embeddings may lose some information about sentence structure and word relationships.

### Recommendations

1. Use a larger and more diverse dataset.
2. Experiment with different similarity thresholds.
3. Compare BERT with models such as Sentence-BERT.
4. Explore alternative pooling techniques for generating sentence embeddings.

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/sangvivy/bert-contextual-embeddings-similarity.git
```

### 2. Navigate to the Project Directory

```bash
cd bert-contextual-embeddings-similarity
```

### 3. Create a Virtual Environment

```bash
python -m venv .venv
```

### 4. Activate the Virtual Environment

**Windows PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

### 5. Install Dependencies

```bash
pip install -r requirements.txt
```

### 6. Launch Jupyter Notebook

```bash
jupyter notebook
```

Open `notebooks/bert_sentence_similarity.ipynb` and run the cells sequentially.

**Note:** The pre-trained BERT model is downloaded from Hugging Face the first time it is loaded, so an internet connection is required.

## Conclusion

This project demonstrates how BERT can be applied to contextual word representation and sentence similarity analysis. The polysemy experiment illustrates how word representations change depending on context, while the sentence similarity experiment achieved 80% accuracy using a fixed cosine similarity threshold.

The practical highlights the value of transformer-based models in NLP and the importance of dataset size, threshold selection, and evaluation when developing semantic similarity systems.