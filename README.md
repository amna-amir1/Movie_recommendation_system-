**🎬 Movie Recommendation System**

User-Based, Item-Based & Item-Based + SVD Comparison

📌 Project Description

This project implements and compares multiple Collaborative Filtering approaches on the MovieLens dataset:

User-Based Collaborative Filtering

Item-Based Collaborative Filtering

Item-Based Collaborative Filtering + SVD

The goal was to evaluate whether applying SVD (Singular Value Decomposition) on the item-based approach improves recommendation performance.

**📂 Dataset**

This project uses the MovieLens 100K dataset provided by:

GroupLens Research

Dataset details:

100,000 ratings

~943 users

~1682 movies

Rating scale: 1–5

Highly sparse (~89%)

Exploratory Data Analysis (EDA)

The following checks were performed before modeling:

- Missing Values

Verified null values

Filled missing release dates

Dropped irrelevant columns

- Rating Distribution

Ratings between 2.5–5 were dominant

Dataset not perfectly normally distributed

- Ratings per User

Few users gave many ratings

Majority gave fewer ratings

Long-tail behavior observed

- Ratings per Movie

Few popular movies received many ratings

Many movies had very few ratings

- Genre Distribution

Some genres dominant

“Unknown” genre had zero entries

- Sparsity Check

User-Item matrix created using pivot table.

Sparsity formula:

Sparsity = 1 - (Observed Ratings / Total Possible Ratings)

Observed sparsity ≈ 89%

This confirms the dataset is highly sparse, which is typical in recommender systems.

**⚙️ Models Implemented**


**Step 1 : User Based Collaborative Filtering **

Cosine similarity computed between users

For each user, top-K similar users identified

Weighted ratings from similar users used to generate recommendations

Evaluation performed using Precision@10, Recall@10, F1@10

📊 Results

Precision@10: 0.282

Recall@10: 0.220

F1@10: 0.205

** Step 2: Item-Based Collaborative Filtering**

Cosine similarity computed between items

For each user, top-K similar items recommended

Evaluation performed using Precision@10, Recall@10, F1@10

**📊 Results**

Precision@10: 0.282

Recall@10: 0.220

F1@10: 0.204

** Step 3: Item-Based CF + SVD**

In this step:

User-Item matrix constructed

User bias removed (mean-centering)

Applied Truncated SVD

Reconstructed matrix

Item similarity computed on reduced latent space

Evaluated using same metrics (Precision@10)

Purpose:
To reduce sparsity effect and capture latent relationships between items.

**📊 Results**

Precision@10: 0.331

Recall@10: 0.234

F1@10: 0.233

**📈 Performance Comparison**

| Model               | Precision@10 | Recall@10 | F1@10  |
| ------------------- | ------------ | --------- | ------ |
| User-Based CF       | 0.2822       | 0.2203    | 0.2048 |
| Item-Based CF       | 0.2822       | 0.2203    | 0.2048 |
| Item-Based CF + SVD | 0.3306       | 0.2338    | 0.2326 |


**📊 Observations**

Applying SVD improved Precision and F1-score.

Recall also slightly improved.

SVD helped capture hidden item relationships.

Sparsity remained high but latent factor modeling reduced its negative impact.

**🔎 Evaluation Method**

Evaluation was done per user:

For each user, top 10 recommendations generated

Compared against relevant items in test set

Precision, Recall, and F1 computed

Final results averaged across all users

** Key Insights**

Item-Based CF works well for sparse datasets.

Adding SVD improves recommendation quality.

Precision improved from 0.282 → 0.331 after SVD.

Latent factor modeling enhances item similarity learning.

** Technologies Used**

Python

Pandas

NumPy

Scikit-learn

Cosine Similarity

**📌 Conclusion**

This project demonstrates that combining Item-Based Collaborative Filtering with SVD improves recommendation performance in sparse datasets.

Although sparsity remains high (~89%), dimensionality reduction helps uncover latent patterns, leading to better precision and overall performance.
