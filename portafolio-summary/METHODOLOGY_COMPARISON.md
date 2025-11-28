# Methodology Comparison: Factor Analysis vs. Discriminant Analysis vs. Cluster Analysis

This document provides a comprehensive comparative analysis of the three multivariate statistical methods applied across the portfolio cases.

---

## Comparative Analysis Table

| **Aspect** | **Factor Analysis** | **Discriminant Analysis** | **Cluster Analysis** |
|---|---|---|---|
| **Learning Type** | Unsupervised | Supervised | Unsupervised |
| **Primary Objective** | Dimensionality reduction; identify latent factors | Classification; predict group membership | Segmentation; identify natural groupings |
| **Required Input** | Continuous variables (survey items, ratings) | Categorical target + continuous predictors | Continuous behavioral/numerical variables |
| **Output** | Latent factors; factor scores; communalities | Discriminant functions; classification probabilities | Clusters; centroids; cluster assignments |
| **Business Use Case** | Simplify survey data; uncover hidden drivers of satisfaction | Predict customer creditworthiness; reduce default risk | Identify customer segments for marketing strategies |
| **Case Study Applied** | Customer Satisfaction Analysis (Case 1) | Credit Risk Prediction (Case 2) | MegaMart Customer Segmentation (Case 3) |
| **Limitations** | Requires large sample size; assumes factor structure; interpretation of factors subjective | Requires labeled training data; assumes homogeneous covariances (LDA); sensitive to outliers | Requires choosing optimal number of clusters; may form artificial groupings; sensitive to scaling |
| **Interpretability** | High (factors represent meaningful latent constructs) | High (discriminant functions are linear combinations of predictors) | High (cluster centroids provide actionable profiles) |
| **Computational Complexity** | Low–moderate; eigendecomposition | Low; closed-form solution (LDA) or iterative (QDA) | Moderate; iterative optimization (K-means) |
| **Model Performance (Case Study)** | R² ≈ 0.64 when predicting satisfaction from factor scores | Accuracy = 100%; AUC = 1.00 (LDA & QDA) | Silhouette Score ≈ 0.317; clear cluster separation on PCA |
| **Number of Features** | Reduces 30+ correlated survey items → 5 interpretable factors | Uses 18 financial/demographic predictors | Works with 9 behavioral dimensions; benefits from PCA for visualization |
| **Handling Missing Data** | Standard listwise deletion or imputation; EM algorithms available | Assumes complete cases; sensitive to missingness in predictors | Handles missing data if imputed; affects centroid stability |
| **Validation Approach** | Scree plot; Kaiser-Meyer-Olkin (KMO) test; Bartlett's test of sphericity | Train-test split; confusion matrix; ROC curve; AUC | Elbow method; Silhouette score; Hierarchical clustering validation |
| **Scalability** | O(p³) for covariance matrix (p = variables); scales well to 100+ variables | O(n × p) for training; fast prediction; scales to large datasets | O(n × p × k × iterations); practical up to millions of records with sampling |

---

## Detailed Comparison by Dimension

### 1. **Unsupervised vs. Supervised Learning**

- **Factor Analysis (Unsupervised):** No target variable required. Discovers structure from patterns in survey responses alone. Ideal when the underlying drivers are unknown.
  
- **Discriminant Analysis (Supervised):** Requires a labeled target (good/bad payers). Uses group membership to find optimal separation boundaries. More powerful when labeled data is available and reliable.

- **Cluster Analysis (Unsupervised):** No predefined groups. Discovers natural groupings based on proximity in feature space. Risk: may find artifacts if groups don't truly exist.

### 2. **Objective & Business Translation**

| Method | What It Finds | Business Insight |
|---|---|---|
| **Factor Analysis** | 5 factors: Technical Excellence, Relationship Trust, Perceived Value, Project Execution, Support Excellence | Prioritize which service dimensions drive renewal and revenue |
| **Discriminant Analysis** | LDA/QDA boundaries separating good from bad payers | Approve/reject loans in seconds based on key financial metrics |
| **Cluster Analysis** | 4 customer segments (High-Value Loyalists, At-Risk Shoppers, Steady Buyers, Browsers) | Tailor marketing, retention, and conversion strategies per segment |

### 3. **Data Requirements**

| Aspect | Factor Analysis | Discriminant Analysis | Cluster Analysis |
|---|---|---|---|
| **Sample Size** | 200–500+ (ideally n:p ≥ 5:1) | 100+ per group; typically 1000+ | 100+; performs better with 1000+ |
| **Data Type** | Continuous or ordinal (Likert scales) | Mixed (continuous + categorical target) | Continuous (or properly scaled ordinal) |
| **Outliers Sensitivity** | Moderate (affects correlations) | High (affects discriminant function) | High (shifts centroids; K-means especially) |
| **Multicollinearity** | Expected & handled via factors | Should be checked; can bias coefficients | Irrelevant; clusters are distance-based |

### 4. **Interpretability & Actionability**

**Factor Analysis:**
- Factors are latent constructs (e.g., "Technical Excellence" loads on technical_expertise, problem_solving, innovation).
- Factor scores can feed into regression models for impact quantification.
- Rotation (Varimax) improves interpretability.

**Discriminant Analysis:**
- Discriminant function shows linear combination of predictors: `D = w₁×X₁ + w₂×X₂ + ...`
- Weights indicate which variables matter most.
- Classification rule is simple: assign to group with highest posterior probability.

**Cluster Analysis:**
- Cluster centroids (means of each variable per cluster) are directly interpretable.
- Cluster profiles (e.g., "Cluster 0: High spend, high engagement, high tenure") translate to personas.
- Allows targeted interventions per cluster.

### 5. **Practical Challenges & Limitations**

| Challenge | Factor Analysis | Discriminant Analysis | Cluster Analysis |
|---|---|---|---|
| **Optimal hyperparameters** | # of factors (scree plot, parallel analysis) | Assumes homogeneous covariance (LDA); QDA relaxes this | Optimal k (elbow method, silhouette, dendrogram) |
| **Interpretability pitfalls** | Subjectivity: two analysts may rotate differently | Perfect separation (as in Case 2) is unrealistic; overfitting risk | Risk of finding clusters that don't generalize |
| **Scalability issues** | O(p³) for large p; variable selection may be needed | Fast; scales well; no curse of dimensionality | K-means converges slowly for large k; sensitive to initialization |
| **Assumptions violated** | Factorability not guaranteed (low KMO); sample size too small | Normality; homogeneity of covariance; no multicollinearity | No formal statistical assumptions; heuristics only |

### 6. **Model Performance Summary from Portfolio Cases**

#### **Case 1: Factor Analysis (Customer Satisfaction)**
- **Variance Explained:** 61.85% of total variance explained by 5 factors
- **Factor 1 Dominance:** ~38% of variance; strongest predictor of satisfaction
- **Regression R²:** 0.64 when predicting satisfaction from factor scores
- **Actionability:** Clear hierarchy of 5 improvement levers for management

#### **Case 2: Discriminant Analysis (Credit Risk)**
- **Accuracy:** 100% (both LDA and QDA achieved perfect separation)
- **AUC:** 1.00 (perfect discrimination)
- **Top Predictors:** Payment history score, job stability, credit utilization
- **Actionability:** Automated approval/rejection rule; immediate deployment

#### **Case 3: Cluster Analysis (Customer Segmentation)**
- **Optimal k:** 4 clusters (validated via dendrogram & silhouette)
- **Silhouette Score:** 0.317 (moderate; acceptable for behavioral data)
- **Largest Segment:** Browsers with Moderate Spend (37.1%)
- **Highest Value:** High-Value Loyalists concentrate ~$104K/year revenue
- **Actionability:** Personalized campaigns per cluster; estimated total ROI impact ~$284K/year

---

## When to Use Each Method

### **Choose Factor Analysis when:**
- You have many correlated variables (surveys, ratings, features) and want to reduce noise
- Goal is to discover underlying latent constructs (what drives satisfaction? brand perception?)
- You need interpretable factors for downstream modeling (regression, SEM)
- Sample size is moderate-to-large (200–1000+)

### **Choose Discriminant Analysis when:**
- You have a clear binary or multi-class target (good/bad, low/med/high risk)
- Goal is to classify new observations into known groups
- You need interpretable decision boundaries and probabilities
- Speed and simplicity are important (LDA is very fast)

### **Choose Cluster Analysis when:**
- You want to discover natural groupings without pre-labeled data
- Goal is customer/market segmentation for personalization
- You expect heterogeneous subgroups within your population
- You need actionable personas or behavioral profiles

---

## Key Takeaways

| Dimension | Winner(s) | Rationale |
|---|---|---|
| **Easiest to interpret** | Cluster Analysis & Factor Analysis | Profiles/factors are human-readable |
| **Most actionable** | Cluster Analysis | Directly leads to marketing/product strategies |
| **Most statistically rigorous** | Discriminant Analysis | Formal assumptions; hypothesis testing framework |
| **Best for high-dimensional data** | Factor Analysis | Reduces dimensionality elegantly |
| **Fastest to deploy** | Discriminant Analysis | Simple decision rule; no retraining needed |
| **Highest business impact (Case Studies)** | Cluster Analysis | $284K ROI from segmentation > 100% accuracy on small dataset |

---

## Conclusion

All three methods are complementary:

1. **Start with Factor Analysis** if your data is exploratory and noisy (many correlated variables).
2. **Use Discriminant Analysis** if you have labeled outcomes and need to automate classification.
3. **Apply Cluster Analysis** if you want to discover and act on natural customer segments.

In the portfolio:
- **Case 1** simplified 30+ survey items → 5 factors → quantified satisfaction drivers
- **Case 2** classified loan applicants with near-perfect accuracy
- **Case 3** identified 4 actionable customer segments with 6-figure revenue impact

Each case demonstrates real-world applicability and business value.

