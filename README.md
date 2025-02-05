# Personalized Information Retrieval

## Project Overview
This project develops a **personalized search engine** for retrieving relevant answers from the **SE-PQA dataset**, a community question-answering (CQA) resource. The goal is to enhance **search results** through personalization, leveraging **user-specific features** such as preferences and contextual data.

### Key Features
- **Traditional Retrieval Models**: Implements **TF-IDF** and **BM25** for baseline performance.
- **Neural Re-Rankers**: Integrates **bi-encoder** and **cross-encoder** models to improve ranking quality.
- **LLM-Based Query Expansion**: Utilizes **Microsoft Phi-3** for personalized query refinement.
- **Recommender System Integration**: Enhances personalization using **content-based filtering** and **popularity-based reranking**.
- **Customizable Search Pipeline**: Allows users to select retrieval and ranking methods based on preferences.

## Dataset
- **SE-PQA dataset** (subset of **10,000 documents**) from **StackExchange**.
- **Metadata** includes **tags, scores, and comment counts** to refine retrieval.
- **Query splits**: 100 training, 100 validation, 100 testing queries.

## Methodology
### 1. Preprocessing
- Lowercasing and punctuation removal.
- Comparison of **stemmed vs. non-stemmed corpora** (minimal preprocessing preferred).

### 2. Retrieval Models
- **TF-IDF & BM25**: Traditional ranking techniques.
- **Neural Re-Rankers**: BERT-based **bi-encoder & cross-encoder** models.
- **LLM Query Expansion**: Generates personalized queries (Microsoft Phi-3 Mini).

### 3. Personalization
- **Quality-based ranking**: Uses answer scores as relevance proxies.
- **Popularity-based ranking**: Leverages comment counts for reranking.
- **Content-based filtering**: Builds **user profiles** based on historical tags and computes **cosine similarity** with retrieved documents.

### 4. Search Pipeline
- Users input **query + user profile**.
- Search retrieves **top 100 documents** using BM25.
- Neural models **re-rank results**.
- Personalization **adjusts final ranking**.

## Evaluation
Metrics used to assess performance:
- **Recall (R@100, R@5)**: Measures retrieval effectiveness.
- **Precision (P@1, AP@100)**: Evaluates ranking quality.
- **nDCG@10, nDCG@3**: Assesses ranking order relevance.

### Performance Highlights
- **Baseline BM25**: Strong recall but weaker top-ranked results.
- **Neural re-rankers**: Significant ranking improvements.
- **Personalization (content + popularity + quality)**: Best performance on **nDCG and P@1**.

## Challenges & Future Work
- **Hardware constraints**: Limited fine-tuning and grid search.
- **LLM Query Expansion Issues**: Lengthened queries reduced performance.
- **Future Directions**:
  - Fine-tune models on SE-PQA data.
  - Optimize weighting combinations.
  - Scale to the full dataset.
  - Enhance content-based ranking techniques.

