# Marketing_Analysis
Rural vs Urban Mobile Phone Consumer Segmentation

->Customer segmentation analysis on rural and urban mobile phone buyers using K-Prototypes clustering — a technique built for datasets that mix numeric and categorical features without forcing everything into one-hot dummy variables.

📌 Overview

Mobile phone buying behavior isn't driven by a single trait — it's a mix of demographics (age, income), spending patterns, and preferences (brand, purchase channel, buying factors). Standard K-Means can't handle categorical variables directly, so this project uses K-Prototypes, which combines K-Means (for numeric features) with K-Modes (for categorical features) into a single distance metric.

The result is a set of consumer segments that can inform targeted marketing, channel strategy, and product positioning across rural and urban markets.

🗂️ Dataset

Rural_vs_Urban_Consumer_Survey_EN_updated.xlsx — survey responses covering:

Numeric features

Age
Monthly Household Income
Amount Spent on Previous Phone (₹)
Usage Before Replacing Previous Phone (Months)
Research Before Purchase (Days)

Categorical features

Location Type (Rural / Urban)
Gender
Current Mobile Phone Brand
Factors For Buying
Preferred Purchase Channel

Note: the raw dataset is not included in this repo. Update the file path in the notebook to point to your own copy before running.

⚙️ Methodology
Data cleaning — dropped empty rows, standardized inconsistent brand/category labels (e.g. Iqoo → IQOO), imputed missing Age values with the median.
Preprocessing — scaled numeric features with StandardScaler; kept categorical features as-is for K-Prototypes' native handling.
Model selection — ran K-Prototypes for k = 2 to 8 and used the elbow method (cost vs. k) to choose the optimal number of clusters.
Final clustering — fit K-Prototypes with k = 3 (Huang initialization, 10 runs) to get stable cluster assignments.
Profiling — computed per-cluster numeric averages and modal categorical values to characterize each segment.
Visualization — reduced dimensions via PCA (on one-hot encoded features) to plot clusters in 2D.
Validation — sanity-checked that spending, research time, and channel preference patterns told a coherent story across clusters.
📊 Key Findings
Segment	Profile
Cluster 0	Older, price-driven buyers, skewed toward Pixel devices
Cluster 1	Long research cycle (~24 days) — risk-averse, price-sensitive, likely comparison-shops across stores/platforms
Cluster 2	Younger, security-focused — likely values data privacy, biometrics, and software updates
Cluster 3	Short research cycle (~8 days) — decisive buyers, possibly more influenced by peer/local recommendations than research
🛠️ Tech Stack
Python 3
pandas, numpy
scikit-learn (StandardScaler, PCA)
kmodes (KPrototypes)
matplotlib
openpyxl
🚀 Getting Started
bash
pip install pandas numpy matplotlib scikit-learn kmodes openpyxl

Open Clustering.ipynb in Jupyter, update the dataset file path in the second cell, and run all cells in order.

📁 Repository Structure
.
├── marketing analysis   # Full analysis: cleaning → clustering → profiling → report
└── README.md
📈 Possible Next Steps
Validate cluster stability with a silhouette-style metric adapted for mixed-type data
Cross-tabulate clusters against Location Type (Rural/Urban) to see how segments map onto the original rural/urban split
Turn cluster profiles into actionable personas for marketing/product teams
