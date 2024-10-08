# Topic Modeling on medium articles

## Overview

This project focuses on analyzing Medium articles using various data processing and visualization techniques. The goal is to extract valuable insights, such as identifying top authors, counting claps, and performing topic modeling using Latent Dirichlet Allocation (LDA).

## Project Structure

### Data Collection
The data used in this project is a CSV file containing Medium articles. Each article includes text, author information, and the number of claps.

```python
medium_articles = pd.read_csv("articles.csv")
```

### Data Exploration

1. **Author Analysis**: 
   - The total number of unique authors is identified.
   - The distribution of articles across authors is visualized.

2. **Clap Analysis**: 
   - The total number of claps for each author is calculated.
   - A histogram displays the top 10 authors by the number of claps received.

### Data Preprocessing

#### 1. Text Preprocessing
The text data is cleaned and prepared for analysis. This involves:
- **Tokenization**: Splitting text into individual words.
- **Lemmatization**: Reducing words to their base forms (e.g., "running" to "run").
- **Stopword Removal**: Eliminating common words that do not contribute to the analysis.

#### 2. Gensim for Topic Modeling
Gensim is used to create a dictionary and corpus, which are essential for LDA topic modeling.

### Topic Modeling with LDA

1. **Dictionary Creation**: A Gensim dictionary is created from the processed text.
2. **Corpus Creation**: The corpus is built, which will be used for LDA modeling.
3. **LDA Model**: An LDA model is created to discover topics within the articles.

```python
lda_model = gensim.models.ldamodel.LdaModel(
    corpus=corpus,
    id2word=id2word,
    num_topics=5,
    random_state=100,
    update_every=1,
    chunksize=100,
    passes=10,
    alpha="auto"
)
```

### Data Visualization

- **Author and Article Count**: A bar chart displays the top authors by the number of articles written.
- **Author and Clap Count**: Another bar chart shows the top authors by the number of claps received.

### LDA Visualization

Using `pyLDAvis`, the topics generated by the LDA model are visualized interactively.

```python
import pyLDAvis.gensim
pyLDAvis.enable_notebook()
vis = pyLDAvis.gensim.prepare(lda_model, corpus, id2word, mds="mmds", R=30)
vis
```

## Installation

To run the project, ensure you have the following Python packages installed:

```bash
pip install matplotlib seaborn nltk pandas gensim pyLDAvis spacy
```

## Usage

1. Load the dataset (`articles.csv`).
2. Execute the preprocessing steps to clean and prepare the data.
3. Perform topic modeling using LDA.
4. Visualize the data and the LDA results.

## Conclusion

This project provides a comprehensive approach to analyzing text data from Medium articles. By leveraging advanced NLP techniques and visualizations, it uncovers insights into the content and engagement of various authors.
