# Emotion Classification Model Comparison

This project compares five pretrained Transformer-based models for emotion classification. The goal is to identify a suitable model for detecting emotions in text before applying it to literary/book analysis.

## Models Tested

1. RoBERTa + GoEmotions
2. DistilRoBERTa Emotion
3. ModernBERT + GoEmotions
4. ModernBERT-Large + GoEmotions
5. RoBERTa-Large Emotion

## Dataset

A labeled dataset containing 50 text samples was used for preliminary validation.

Each sample contains:

* `text` — input sentence
* `emotion` — actual emotion label

Example:

```text
text: I am so happy that I finally achieved my goal!
emotion: joy
```

## Methodology

The same dataset was given to all five pretrained models.

For each text:

```text
Input Text
    ↓
Emotion Classification Model
    ↓
Predicted Emotion
    ↓
Compare with True Emotion
    ↓
Evaluation Metrics
```

The highest-probability emotion predicted by each model was selected as the final prediction.

## Evaluation Metrics

The models were compared using:

* Accuracy
* Precision
* Recall
* Macro F1-score
* Weighted F1-score
* Confusion Matrix
* Per-emotion performance

## Results

| Model                         | Accuracy |  Macro F1 | Weighted F1 |
| ----------------------------- | -------: | --------: | ----------: |
| RoBERTa + GoEmotions          |      76% |     0.571 |       0.747 |
| DistilRoBERTa Emotion         |      52% |     0.189 |       0.395 |
| **ModernBERT + GoEmotions**   |  **82%** | **0.678** |   **0.832** |
| ModernBERT-Large + GoEmotions |      80% |     0.635 |       0.803 |
| RoBERTa-Large Emotion         |      52% |     0.188 |       0.391 |

## Best Performing Model

In this preliminary experiment, **ModernBERT + GoEmotions** achieved the highest performance:

* Accuracy: **82%**
* Macro F1: **0.678**
* Weighted F1: **0.832**

Therefore, ModernBERT + GoEmotions was selected for the next stage of the project.

## Book Emotion Analysis

The selected model will be used to analyze emotions in books at the sentence or paragraph level.

The planned workflow is:

```text
Book
 ↓
Text Preprocessing
 ↓
Sentence / Paragraph Segmentation
 ↓
Emotion Detection
 ↓
Dominant Emotion
 ↓
Emotion Distribution
 ↓
Emotion Progression
 ↓
Book-Level Analysis
```

The analysis can be used to study:

* Dominant emotions in paragraphs
* Emotion changes across chapters
* Emotion progression throughout a book
* Differences in emotional patterns between books
* Relationship between emotions and topics


## Technologies

* Python
* PyTorch
* Hugging Face Transformers
* Scikit-learn
* Pandas
* Matplotlib
* Google Colab

## How to Run

Open the notebook in Google Colab:

```text
notebooks/Five_Emotion_Models_Comparison.ipynb
```

Install the required libraries:

```bash
pip install transformers torch scikit-learn pandas matplotlib seaborn accelerate
```

Upload:

```text
emotion_test_dataset.csv
```

Then run the notebook cells to generate predictions and evaluation results.

## Note

The reported results are based on a small 50-sample dataset and should be considered preliminary. A larger standardized dataset is required for reliable model validation.
