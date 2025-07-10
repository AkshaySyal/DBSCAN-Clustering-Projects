# DBSCAN-Clustering-Projects
The project implements and evaluates DBSCAN across toy, synthetic, and real-world datasets, highlighting its clustering process, parameter sensitivity, and performance strengths and limitations.

# Problem Statement - 1
<img width="1174" height="88" alt="image" src="https://github.com/user-attachments/assets/4d7438fa-c19d-4203-9e36-cbebb6d0cb9d" />

# Solution Summary
- Implemented a **custom DBSCAN clustering algorithm** and applied it to three 2D toy datasets:
  - **Circles**
  - **Blobs**
  - **Moons**

- **Algorithm Details**:
  - `RangeQuery` function:
    - Finds all neighbors within `eps` by iterating over all points.
    - Results in **O(N²)** complexity for neighbor search.
  - `DBSCAN` function:
    - Processes each point:
      - Fewer than `minPts` neighbors → labeled as noise (`cluster = -1`).
      - Core point (`≥ minPts` neighbors) → starts/expands a cluster.
    - Recursively grows clusters, reassigning reachable noise points.

- **Parameter Selection**:
  - `minPts` fixed at **3** (d + 1 for 2D).
  - `eps` determined using `findEps` function:
    - Uses a **KD-Tree** to compute 3rd nearest neighbor distances.
    - Plots histogram to **visually guide** eps selection.
    - Selected values:
      - Circles → **0.07**
      - Blobs → **0.125**
      - Moons → **0.14**

- **Key Insights**:
  - Demonstrated hands-on understanding of **DBSCAN’s mechanics**.
  - Showcased systematic **eps selection** based on data density.
  - Highlighted DBSCAN’s strength in identifying **arbitrary-shaped clusters** and distinguishing noise.

- **Visualization**:
  - Used `matplotlib.pyplot` and `seaborn` in `plotResult` function.
  - Color-coded points by **cluster ID**, with a distinct color for noise.
  - Provided intuitive visual interpretation of clustering output.

- **Conclusion**:
  - Custom DBSCAN implementation effectively clustered diverse 2D datasets.
  - Emphasized both technical and visual understanding of density-based clustering.


# Problem Statement - 2
<img width="1474" height="147" alt="image" src="https://github.com/user-attachments/assets/fe58753e-b04c-4b67-808b-7561411c15c0" />
- Implemented a **comprehensive custom DBSCAN algorithm** and applied it to three real-world datasets:
  - **20 Newsgroups (20NG)**
  - **Fashion-MNIST (Fashion)**
  - **UCI Household Power Consumption (HouseHold)**

- **Algorithm Details**:
  - Two-phase implementation:
    1. **Neighborhood creation**:
       - `RangeQuery` function using **BallTree** (with KDTree as an alternative) for efficient neighbor search within `eps`.
    2. **Clustering logic**:
       - Iteratively processes points:
         - Fewer than `minPts` neighbors → labeled as noise (`cluster = -1`).
         - Core point (`≥ minPts` neighbors) → starts/expands a cluster.
       - Recursively grows clusters, reassigning reachable noise points.

- **Parameter Selection**:
  - Used `determineEpsAndMinPts` function:
    - Calculated and plotted **k-th nearest neighbor distances**.
    - Visually selected `eps`; set `minPts = k`.
  - Selected parameters:
    - Fashion → **eps = 1200**, **minPts = 3** (Euclidean)
    - Household → **eps = 2.5**, **minPts = 8** (Euclidean)
    - 20NG → **eps = 0.9**, **minPts = 5** (Jaccard metric)

- **Evaluation & Insights**:
  - Assessed clustering quality using **purity metric**.
  - Demonstrated ability to uncover **natural groupings** and distinguish **noise** in diverse, high-dimensional datasets.
  - Highlighted systematic approach for parameter tuning across different data types.

- **Conclusion**:
  - Custom DBSCAN successfully scaled from toy datasets to real-world datasets.
  - Showcased both technical rigor and adaptability to different domains and data structures.


# Solution Summary

