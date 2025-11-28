# Portfolio MA2003B — Application of Multivariate Methods in Data Science

[![Actions Status](https://img.shields.io/github/actions/workflow/status/Sophiaalbarran/portfolio-ma2003b/ci.yml?branch=main)](https://github.com/Sophiaalbarran/portfolio-ma2003b/actions)
[![Top Language](https://img.shields.io/github/languages/top/Sophiaalbarran/portfolio-ma2003b)](https://github.com/Sophiaalbarran/portfolio-ma2003b)
[![License](https://img.shields.io/github/license/Sophiaalbarran/portfolio-ma2003b)](LICENSE)

This repository contains the final portfolio for the course **MA2003B — Application of Multivariate Methods in Data Science**. It brings together three case studies applied to real business problems, focusing on multivariate analysis, reproducible Python workflows, and data-driven communication.

The portfolio aims to demonstrate technical competencies (data preprocessing, modeling, validation, and visualization) and the ability to translate quantitative findings into actionable recommendations for stakeholders.

Each case includes business context, research questions, applied methodology, reproducible notebooks, key visualizations, and conclusions.

---

**Team**

| Member | Student ID | Profile |
|---|---:|---|
| **Sibyla Vera Avila** | A01665122 | https://www.linkedin.com/in/sibyla-vera-%C3%A1vila-46109a326/ |
| **Sophia Gabriela Martínez Albarrán** | A01424430 | https://www.linkedin.com/in/sophiamartinezalbarran |
| **Regina Pérez Vázquez** | A01659356 | https://www.linkedin.com/in/regina-p%C3%A9rez-v%C3%A1zquez-130569364 |

> Note: Update names, student IDs and profile links if there are any changes.

---

**Table of Contents**

- [Title and description](#portfolio-ma2003b---application-of-multivariate-methods-in-data-science)
- [Team](#team)
- [Case study summary](#case-study-summary)
- [Reproducibility instructions](#reproducibility-instructions)
- [Repository structure](#repository-structure)
- [License](#license)

**Direct links to case studies**

- [Case 1 — Customer Satisfaction (Factor Analysis)](case-01-factor-analysis/README.md)
- [Case 2 — Credit Risk (Discriminant Analysis)](case-02-discriminant-analysis/README.md)
- [Case 3 — MegaMart Customer (Segmentation)](caso-03-megamart-customer/README.md)

---

## Case Study Summary

| Case | Method | Business question | Key finding | Link |
|---|---|---|---|---|
| Customer Satisfaction Analysis | Exploratory Factor Analysis (EFA) | Which latent dimensions drive customer satisfaction? | Five main factors explain most of the variance; service quality is the strongest driver. | [View case](case-01-factor-analysis/README.md) |
| Credit Risk (LendSmart) | Discriminant Analysis (LDA/QDA) | How to classify applicants by credit risk? | Discriminant models indicate stable income and credit behavior are strong predictors of risk. | [View case](case-02-discriminant-analysis/README.md) |
| MegaMart Customer Segmentation | K-Means & Hierarchical Clustering | What customer segments exist and how to prioritize them? | Four actionable segments were identified; a high-value segment concentrates most spend. | [View case](caso-03-megamart-customer/README.md) |

---

## Reproducibility Instructions

**Software requirements**

- Python 3.8+ (3.10 recommended)
- `pip` or `venv`/`virtualenv`

Required Python packages are listed in `requirements.txt`. To create an environment and reproduce the notebooks:

1. Clone the repository:

```bash
git clone https://github.com/Sophiaalbarran/portfolio-ma2003b.git
cd portfolio-ma2003b
```

2. Create and activate a virtual environment (macOS / Linux):

```bash
python3 -m venv .venv
source .venv/bin/activate
```

3. Install dependencies:

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

4. Open the notebooks with Jupyter Lab/Notebook:

```bash
jupyter lab
# or
jupyter notebook
```

5. Execute notebooks (examples):

```bash
# Case 1
jupyter nbconvert --to notebook --execute case-01-factor-analysis/notebooks/factor_analysis.ipynb --output case-01-executed.ipynb

# Case 2
jupyter nbconvert --to notebook --execute case-02-discriminant-analysis/notebooks/credit_risk_analysis.ipynb --output case-02-executed.ipynb

# Case 3
jupyter nbconvert --to notebook --execute caso-03-megamart-customer/notebooks/retail.ipynb --output case-03-executed.ipynb
```

> If a kernel fails due to version mismatches, create a kernel with `python -m ipykernel install --user --name portfolio-env` and select it in Jupyter.

---

## Repository Structure

Brief tree and description of main folders:

```
mi-portfolio-ma2003b/
│
├── README.md                          # Project overview (this file)
├── LICENSE                            # MIT license
├── .gitignore                         # Git ignore rules
├── requirements.txt                   # Project Python dependencies
│
├── case-01-factor-analysis/
│   ├── README.md                      # Key findings and links for case 1
│   ├── data/
│   │   ├── customer_satisfaction_data.csv
│   │   └── DATA_DICTIONARY.md
│   ├── notebooks/
│   │   └── factor_analysis.ipynb
│   ├── reports/
│   │   ├── executive_summary.pdf
│   │   └── technical_report.pdf
│   ├── src/
│   │   └── utils.py
│   └── visualizations/
│       ├── correlation_heatmap.png
│       ├── scree_plot.png
│       └── factor_loadings.png
│
├── case-02-discriminant-analysis/
│   ├── README.md
│   ├── data/
│   ├── notebooks/
│   ├── reports/
│   └── visualizations/
│
├── case-03-cluster-analysis/
│   ├── README.md
│   ├── data/
│   ├── notebooks/
│   ├── reports/
│   └── visualizations/
│
├── portfolio-summary/
│   ├── PORTFOLIO_OVERVIEW.md
│   ├── LESSONS_LEARNED.md
│   └── METHODOLOGY_COMPARISON.md
│
└── presentation/
    └── final_portfolio_presentation.pdf
```


**Short folder descriptions**

- **case-01-factor-analysis/** → Complete factor analysis case: data, notebook, reports and visualizations.  
- **case-02-discriminant-analysis/** → LDA/QDA models, notebooks, results and plots.  
- **caso-03-megamart-customer/** → Customer segmentation with K-Means and hierarchical clustering, visualizations and reports.  
- **portfolio-summary/** → Executive summary, lessons learned, and methodological comparison.  
- **presentation/** → Final portfolio presentation in PDF.  
- **requirements.txt** → Dependency list required to reproduce the analysis.  

---

## License

This project is licensed as indicated in the `LICENSE` file.

---

