# Rainfall Data Quality Control (QC) Framework!

<img width="1889" height="853" alt="image" src="https://github.com/user-attachments/assets/0a7d7d45-0dda-4ca1-8d93-e0f4b573d2ad" />

The data processing workflow is divided into three hierarchical stages to ensure the highest reliability of rainfall records:

# 1. Basic Quality Control

The initial phase focuses on the structural and physical integrity of the raw data for each station.

 - 1.1 Data Validation: Verification of file formats and column structures.
 - 1.2 Data Verification: Identification and removal of duplicate records.
 - 1.3 Data Cleansing: * Physical Limits Check: Ensuring values fall within plausible meteorological ranges.
		    Threshold Review: Specialized screening for extreme daily rainfall values.

# 2. Advanced Quality Control (Quality Indexing)

This stage evaluates the temporal reliability of the time series using a multi-criteria Quality Index (Q).

 - 2.1 Temporal Consistency (Qgaps): Analyzing data continuity and gaps.
 - 2.2 Data Completeness (P): Assessing the availability of data over the study period.
 - 2.3 Descriptive Statistics Review: Monitoring zero-rainfall patterns via Monthly (Qmzero) and Weekly (Qwzero) Zero Indices.
 - 2.4 Outlier Detection (Qoutliers): Identifying statistical anomalies.

Quality Index calculation: Q = \frac{1}{5} (Qgaps + P + Qmzero + Qwzero + Qoutliers)

# 3. Spatial Consistency Check

The final stage validates data by comparing records with neighboring stations to detect spatial anomalies.

 - 3.1 Step 1: Representativeness (R): Establishing relationships between candidate and auxiliary stations.
 - 3.2 Step 2: Relative Difference (Dif) & Threshold (T): Computing daily pairwise differences against dynamic thresholds.
 - 3.3 Step 3: Weighted Mean (Wm): Aggregating spatial flags to determine the final validity of each data point.

Daily records are then labeled according to their weighted agreement (Wm): 
•	Valid if 𝑊𝑚 ≥ 50%;
•	Doubtful if 20% ≤ 𝑊𝑚 < 50%;
•	Invalid if 𝑊𝑚 < 20%;
•	Insufficient if auxiliaries < 3 (or zero weight).
