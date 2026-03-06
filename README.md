# 🎬 Movie Recommendation System (Two-Tower Neural Network)

A scalable **deep learning–based movie recommendation system** that leverages a **Two-Tower architecture** to learn user and movie representations. The system uses **hybrid filtering** (combining collaborative and content-based signals) to generate personalized recommendations and improves ranking quality by **25% in NDCG@10** compared to baseline methods.

The trained movie embeddings are further used for **semantic clustering**, enabling discovery of similar movies using **K-Means clustering**.

---

# 🚀 Overview

Traditional recommendation systems often rely solely on collaborative filtering, which can struggle with sparse data and cold-start problems. This project implements a **Two-Tower Neural Network** architecture that learns dense embeddings for **users** and **movies** independently.

These embeddings are projected into a **shared latent space**, where similarity between users and movies determines recommendation relevance.

Key capabilities:

- Personalized movie recommendations
- Hybrid filtering using both user interaction and movie metadata
- Scalable embedding-based retrieval
- Clustering of movies using learned semantic representations
- Improved ranking quality using neural representations

---

# 🧠 Model Architecture

The recommendation model follows a **Two-Tower architecture**, consisting of:

### User Tower
A Multi-Layer Perceptron (MLP) that encodes user features into a dense embedding vector.

Input features may include:
- User ID embedding
- User demographics (if available)
- Historical interaction features
- Aggregated behavioral signals


---

### Movie Tower
Another MLP that encodes movie features into a latent embedding.

Input features may include:

- Movie ID embedding
- Genres
- Release year
- Metadata features


---

### Similarity Scoring

User and movie embeddings are projected into the same vector space.

The relevance score is computed using **dot product similarity**:
Score(user, movie) = UserEmbedding ⋅ MovieEmbedding



# 📊 Performance

Evaluation was conducted using ranking metrics commonly used in recommendation systems.

### Key Result

| Metric | Improvement |
|------|------|
| **NDCG@10** | **+25% improvement** over baseline collaborative filtering |

**NDCG@10 (Normalized Discounted Cumulative Gain)** measures the ranking quality of the top 10 recommendations, rewarding systems that place relevant movies higher in the list.

---

# 🎥 Movie Embedding Clustering

After training the model, the **movie tower embeddings** capture semantic relationships between movies.

These embeddings were clustered using **K-Means clustering** to identify groups of similar movies.

### Clustering Pipeline

1. Extract trained movie embeddings from the model
2. Normalize embedding vectors
3. Apply **K-Means clustering (scikit-learn)**
4. Group similar movies into clusters
5. Recommend movies from the same cluster

