# Literary Emotion Analysis Using ModernBERT-GoEmotions

## Project Overview

This project analyzes emotional patterns in literary books obtained directly from **Project Gutenberg**.

The notebooks follow this pipeline:

**Project Gutenberg book → text cleaning → chapter segmentation → paragraph segmentation → sentence segmentation → ModernBERT-GoEmotions → emotion probabilities → sentence/paragraph analysis → visualization**

The project keeps the original **28 GoEmotions labels** and uses sigmoid probabilities because GoEmotions is a multi-label emotion classification task.

## Books Analyzed

| Book | Project Gutenberg ID | Notebook |
|---|---:|---|
| Pride and Prejudice | 1342 | `1342.ipynb` |
| Frankenstein | 84 | `84 (1).ipynb` |
| Alice's Adventures in Wonderland | 11 | `11 (1).ipynb` |
| The Adventures of Sherlock Holmes | 1661 | `1661 (1).ipynb` |

## Model

**Model:** `cirimus/modernbert-base-go-emotions`

The model produces probabilities for the 28 GoEmotions categories:

- admiration
- amusement
- anger
- annoyance
- approval
- caring
- confusion
- curiosity
- desire
- disappointment
- disapproval
- disgust
- embarrassment
- excitement
- fear
- gratitude
- grief
- joy
- love
- nervousness
- optimism
- pride
- realization
- relief
- remorse
- sadness
- surprise
- neutral

`neutral` is retained in the underlying predictions, while the main emotion-flow analysis focuses on non-neutral emotions.

## Main Sentence-Level Analysis

The current sentence-level analysis contains **two separate emotion-flow plots**.

### Plot 1

- Selects 20 eligible paragraphs using a fixed random seed.
- Extracts every sentence from those paragraphs.
- Assigns each sentence its dominant emotion.
- Plots the emotion sequence sentence-by-sentence.
- Paragraph boundaries are shown with vertical dashed lines.

### Plot 2

- Selects a different 20 eligible paragraphs.
- The second set does not overlap with the first set.
- Extracts every sentence from those paragraphs.
- Uses the same sentence-level dominant-emotion procedure.
- Produces a second independent emotion trajectory.

Therefore, both plots represent:

**Sentence number → dominant emotion**

but they are calculated from two different sets of 20 paragraphs.

## Additional Analysis in the Notebooks

The notebooks also contain broader book-level analysis, including:

- 28 emotion probability outputs
- selection of the strongest non-neutral emotions
- paragraph-level dominant emotion
- full-book paragraph emotion flow
- dominant emotion counts across the book
- environmental/context categories
- environmental topic flow
- environmental topic presence

Environmental categories used in the notebook include:

- Nature / Landscape
- Built / Indoor
- Weather / Atmosphere
- Social Environment
- Time / Season
- Movement / Travel

## Data Source

Books are downloaded directly from **Project Gutenberg** using the Gutenberg ebook ID.

No pre-generated book CSV is required.

The notebook performs:

1. Download
2. Gutenberg header/footer removal
3. Chapter detection
4. Paragraph extraction
5. Sentence extraction
6. Emotion inference

## Running the Project

Open any `.ipynb` file in **Google Colab**.

Recommended execution order:

1. Open the notebook.
2. Run the cells from top to bottom.
3. Allow the required Python packages to install.
4. If the notebook asks for a Colab runtime restart after removing `torchvision`, choose **Runtime → Restart session**.
5. Run the notebook from the beginning again.
6. Wait for the ModernBERT model to load.
7. Run the emotion inference cells.
8. Run the visualization cells.

GPU execution is recommended for faster Transformer inference.

## Project Files

```text
capstone/
├── 1342.ipynb
├── 84 (1).ipynb
├── 11 (1).ipynb
├── 1661 (1).ipynb
└── book.pptx
```

## Research Interpretation

The model probabilities are **computational predictions** and should not be interpreted as direct measurements of an author's or character's psychological state.

Environmental categories are based on observable textual/context cues. They should not be interpreted as proof of complete literary or environmental understanding.

Emotion and environmental relationships should be interpreted as **associations**, not causal relationships.

## Purpose

The project is designed to study how emotional patterns vary across literary text and to provide a reproducible sentence-level visualization that can be compared across multiple books.
