FIFA Player Scouting Recommender

## Overview

**ScoutIQ** is a machine learning-powered tool designed to assist soccer team managers and scouts in identifying undervalued or lesser-known players with similar skillsets to top-tier athletes. By leveraging clustering algorithms and similarity metrics, ScoutIQ finds "hidden gems" in the FIFA 2024 player dataset—young, low-cost players who resemble star players in both physical and technical attributes.

## Objectives

- Help clubs scout affordable talent with similar play styles to elite players.
- Compare clustering techniques (K-Means vs. HDBSCAN) to find the best fit for real-world scouting.
- Evaluate performance of clustering models based on silhouette scores and visual PCA projections.

## Dataset

- FIFA 2024 player dataset (~17,000 players)
- Features: ~50 total, including height, stamina, strength, skill ratings, etc.
- Metadata: Name, age, overall rating, potential, position, value

## Technologies Used

- Python (Jupyter Notebook)
- `scikit-learn` for preprocessing, KNN, K-Means, PCA
- `HDBSCAN` for density-based clustering
- `matplotlib` & `seaborn` for data visualization

## Methodology

1. **Preprocessing**:
   - Filtered the dataset to include younger and lower-value players.
   - Selected key physical and skill-based attributes.
   - Standardized feature values using `StandardScaler`.

2. **K-Nearest Neighbors (KNN)**:
   - Retrieved top 1000 players closest to a target star player based on skill and physical similarity.

3. **K-Means Clustering**:
   - Applied to the KNN subset to group players by play style.
   - Cluster count varied from 3–10; evaluated using silhouette scores.

4. **HDBSCAN Clustering**:
   - Applied to the same KNN subset without needing to predefine the number of clusters.
   - Tuned `min_cluster_size` and `min_samples` for performance.
   - Automatically handled noise and outliers.

5. **Visualization**:
   - Used PCA to reduce dimensionality and visually inspect clusters.
   - Compared results for average-tier vs. elite-tier players.

## Key Findings

- **HDBSCAN** handled average players better, identifying meaningful clusters and filtering noise.
- **K-Means** worked more consistently for elite players (e.g., Messi, Ronaldo), where HDBSCAN struggled due to uniqueness.
- Clustering results matched expert expectations: similar players grouped by position, skillset, and value.

## Sample Results

- **Target**: Kieran Trippier  
  → Top Matches: Davies, Aurier, Alexander-Arnold (via K-Means and HDBSCAN)

- **Target**: Neymar Jr.  
  → K-Means matches: Mbappé, Salah, Dybala, Son  
  → HDBSCAN labeled as noise due to outlier stats

## Project Report

For a detailed breakdown of methods, results, and interpretation:
📄 [Read Full Project Report (PDF)](./FIFA%20Scouting%20Recommender%20Project%20Report.pdf)

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/FIFA-Scouting-Recommender.git
   cd FIFA-Scouting-Recommender
   ```
2. Open the notebook:
   ```bash
   jupyter notebook FIFA_Scouting_Recommender.ipynb
   ```
or if using JupyterLab:
  ```bash
  jupyter lab FIFA_Scouting_Recommender.ipynb
  ```
3. Select a star player from the dataset and run the notebook cells.
   - The notebook will:
     - Identify the 1000 most similar players using KNN
     - Cluster them using both K-Means and HDBSCAN
     - Display PCA visualizations and similarity rankings

4. Review the output:
   - PCA plots showing how players are grouped
   - Ranked lists of similar players by cluster
   - Silhouette scores for evaluating clustering quality

## File Structure

FIFA-Scouting-Recommender/
│
├── FIFA_Scouting_Recommender.ipynb             # Main notebook with all code
├── FIFA Scouting Recommender Project Report.pdf  # Summary report
└── README.md                                   # This file


## Future Work

- Add an interactive web interface for dynamic player selection and visualization
- Incorporate additional metrics like market trends and injury history
- Explore deep learning embeddings for improved similarity analysis
- Expand clustering validation using domain expert input and external benchmarks

## License

This project is intended for educational and non-commercial use only.  
© 2025 Titus Lee, Logan Richardson, and Gary Park.

---

📫 For inquiries, feedback, or collaboration, feel free to reach out:  
- [Titus Lee on GitHub](https://github.com/titushyunkyu)  
- [Titus Lee on LinkedIn](https://www.linkedin.com/in/titushyunkyu)
