# DBSCAN on Mall Customers

Small project showing how DBSCAN works on the Mall Customers dataset using annual income and spending score.

## 1. Algorithm (DBSCAN)

- Density-based clustering algorithm.
- Main params:
  - `eps`: neighborhood radius
  - `min_samples`: minimum points to count as “dense”
- Points get labeled as:
  - Core, border, or noise (`-1`).
- No need to specify number of clusters.

## 2. Data & Preprocessing

- Dataset: **Mall Customers**  
  Loaded directly from GitHub:

  - `Annual Income (k$)`
  - `Spending Score (1-100)`

- Only those two columns are used.
- Features are standardized with `StandardScaler` before running DBSCAN.

## 3. Model / Training Scheme

- Use `NearestNeighbors` with `k = 5` to build a k-distance graph.
- Plot sorted 5th-neighbor distances and pick `eps` around the elbow.
- Final DBSCAN settings in the code:
  - `eps = 0.365`
  - `min_samples = 5`
- Extra visualization:
  - Find a strong core point.
  - Draw its epsilon neighborhood and highlight neighbors to show how DBSCAN decides density.

## 4. Evaluation

- After fitting DBSCAN, the script prints:
  - Number of clusters.
  - Number of noise points.
  - Noise ratio.
- Final plot:
  - Different color/marker per cluster.
  - Noise shown in black with `x` markers.

## 5. How to Run

### Dependencies

`requirements.txt`:

```txt
numpy >= 1.23
pandas >= 1.5
matplotlib >= 3.6
seaborn >= 0.12
scikit-learn >= 1.2
```

### Steps (Jupyter Notebook)

```bash
python -m venv .venv
source .venv/bin/activate      # macOS / Linux
# .\.venv\Scripts\activate     # Windows

pip install -r requirements.txt
jupyter notebook
```

Open the notebook file (e.g. analysis.ipynb) in the Jupyter UI.

Run all cells from top to bottom.

The plots (raw data, k-distance graph, epsilon neighborhood, final clusters) will show inline.

Cluster stats will print in the notebook output cells.
