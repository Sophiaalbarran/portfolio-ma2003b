# Lessons Learned

This document summarizes the main technical challenges we faced during the portfolio, interpretation issues we encountered when turning statistical results into business insights, the core lessons learned from the course, and how we plan to apply these methods in our future professional work.

---

## 1. Technical challenges and how we addressed them

- Data quality and missing values:
	- Challenge: Real datasets had missing entries, inconsistent formats, and noisy responses (survey items and behavior logs).
	- How we addressed it: Systematic EDA, column-type normalization, and multiple imputation where appropriate; for some analyses we used listwise deletion only after verifying it did not bias results. We documented cleaning steps in notebooks for reproducibility.

- Factorability and choosing the number of factors (Case 1):
	- Challenge: Determining whether the survey was suitable for factor analysis and how many latent factors to retain.
	- How we addressed it: We computed KMO and Bartlett's tests, inspected the scree plot, and compared parallel analysis results; we also validated factor interpretability by inspecting rotated loadings and cross-checking factor scores in regressions.

- Scaling and feature engineering for clustering (Case 3):
	- Challenge: Variables on different scales caused centroid distortion; raw behavioral metrics needed transformation.
	- How we addressed it: Standardized features (z-score), used log transforms for skewed spend variables, and applied PCA for visualization and dimensional inspection before clustering.

- Choosing k and cluster stability:
	- Challenge: Selecting a stable, business-meaningful number of clusters.
	- How we addressed it: We combined hierarchical clustering (dendrogram) with the elbow method, silhouette scores, and repeated K-Means runs with different seeds to test stability; final clusters were validated against business KPIs.

- Class imbalance and separation issues in discriminant analysis (Case 2):
	- Challenge: Imbalanced classes and almost-perfect separation risk overfitting and unrealistic performance estimates.
	- How we addressed it: Used stratified train-test splits, cross-validation, inspected confusion matrices and ROC curves, and recommended monitoring in production (periodic recalibration and retraining). We also considered simpler rule-based filters as a safety layer in deployment.

- Outliers and influence on models:
	- Challenge: Extreme values heavily influenced LDA/QDA coefficients and cluster centroids.
	- How we addressed it: We flagged and inspected outliers, used robust scaling when needed, and ran sensitivity analyses excluding influential points to compare model stability.

- Reproducibility and environment management:
	- Challenge: Ensuring other users can run the notebooks with the same package versions.
	- How we addressed it: Added `requirements.txt`, documented Python version and suggested creating a `venv`; notebooks include a small environment section and we documented kernel setup instructions.

---

## 2. Interpretation challenges: translating statistical findings into business insights

- Labeling latent constructs from factor loadings:
	- Challenge: Rotated factor loadings can be ambiguous; mapping them to clear business concepts required judgement.
	- Solution: We grouped highest-loading items, wrote plain-language factor labels (e.g., "Technical Excellence"), and validated labels with subject-matter experts.

- Communicating effect sizes and practical impact:
	- Challenge: Stakeholders care about dollars and decisions, not just p-values or loadings.
	- Solution: Converted coefficients and factor-score regressions into expected changes in business KPIs (e.g., predicted increase in renewal likelihood), and produced one-page summaries and visuals highlighting practical implications.

- Turning clusters into actionable personas:
	- Challenge: Raw cluster statistics are not directly operational for marketing teams.
	- Solution: Created short persona descriptions (e.g., "High-Value Loyalists"), provided prioritized actions per persona, and estimated potential revenue impact to motivate adoption.

- Managing overconfidence from perfect metrics:
	- Challenge: Case 2 showed near-perfect accuracy; stakeholders may assume zero risk after deployment.
	- Solution: We emphasized model limitations, performed stress tests, suggested guardrails (human oversight and thresholds), and documented monitoring plans.

---

## 3. Key takeaways (3–5 main lessons)

1. Reproducibility is essential: clean code, environment files, and clear notebook narration make results trustworthy and shareable.
2. Method choice must follow the business question: use factor analysis to explain and compress, discriminant methods to classify with labeled outcomes, and clustering to discover segments for targeted action.
3. Data preparation (cleaning, scaling, and feature engineering) is often the most time-consuming — but it determines model quality more than the choice of algorithm.
4. Translate statistics into business language: visuals, effect-size translation, and short executive summaries are required for stakeholder buy-in.
5. Validate and monitor models in production: cross-validation, stability checks, and periodic recalibration avoid model decay and business risk.

---

## 4. Future applications: how we will use these methods professionally

- Product & customer analytics:
	- Use clustering to define customer personas for personalization, and factor scores as compact features in churn or CLV models.

- Risk & credit scoring:
	- Apply discriminant analysis (or related classification methods) for quick, interpretable scoring models; combine with monitoring dashboards and explainability techniques.

- Survey and market research:
	- Use factor analysis to summarize large questionnaires into actionable themes that feed into product roadmaps and executive KPIs.

- Cross-functional collaboration:
	- Translate technical outputs into one-page recommendations for marketing, product, and finance teams to enable data-driven decisions.

---
