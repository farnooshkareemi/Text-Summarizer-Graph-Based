# TextRank Summarizer 

This repository contains a **from-scratch implementation of the TextRank algorithm**
for **extractive text summarization**, developed as part of the  
**Stochastics and Data Science** course at the **University of Turin**.

The project implements the complete summarization pipeline **without using any external NLP or numerical libraries**, relying only on **pure Python and standard data structures** to ensure full transparency and interpretability.

---

## 📄 Project Overview

TextRank is a graph-based ranking algorithm inspired by PageRank.  
In this project, sentences are modeled as nodes in a weighted similarity graph, where edges represent lexical similarity. Sentence importance emerges through a **random-walk process on the graph**, and the final summary is produced by selecting the most central sentences.

To reduce redundancy, **Maximal Marginal Relevance (MMR)** is applied on top of TextRank scores, balancing relevance and diversity in the extracted summary.

---

## ⚙️ Methodology

The implemented pipeline consists of the following stages:

1. **Manual Preprocessing**
   - Rule-based sentence segmentation (no regex, no NLP libraries)
   - Token cleaning, stopword removal, case normalization
   - Handling abbreviations, decimals, and hyphenated words

2. **Sentence Similarity Computation**
   - Jaccard similarity
   - Cosine similarity with Term Frequency (TF)
   - Cosine similarity with TF–IDF weighting (default choice)

3. **Graph Construction**
   - Dense similarity matrix → sparse graph via threshold τ
   - Row-stochastic transition matrix with dangling-node handling

4. **TextRank Scoring**
   - PageRank-style power iteration
   - Damping factor and convergence monitoring

5. **Sentence Selection**
   - Top-k extraction
   - MMR-based relevance–diversity optimization

---

## 🧪 Experiments

- **Toy example** (news-style article) to illustrate each algorithmic step
- **Real-world evaluation** on a small sample from the CNN/DailyMail dataset
- Analysis of:
  - Edge threshold (τ)
  - Damping factor (d)
  - MMR trade-off parameter (λ)
- Computational complexity and runtime analysis

---

## 📊 Key Properties

- Fully **unsupervised**
- **No external libraries** (no NumPy, no NLTK, no sklearn)
- Completely **interpretable and auditable**
- Modular design: Graph, TextRank, and MMR components separated
- Suitable for educational and algorithmic analysis purposes

---



