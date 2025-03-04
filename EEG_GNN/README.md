# Graph Neural Network-based Classification of Major Psychiatric Disorders using EEG Source Connectivity

- 2024.04 - 현재
- 개인 프로젝트
- 석사 학위 졸업 논문

<hr style="width: 100%; border: 1px solid #ddd;">

## Abstract
This study classifies four groups—healthy controls, bipolar disorder, depressive disorder, and schizophrenia—using EEG source connectivity data from 477 subjects. Convolutional neural networks (CNN) and traditional machine learning methods, such as Random Forests and Support Vector Machines (SVM), often fail to capture spatial relationships and connectivity patterns. To overcome these limitations, we transform connectivity data into graph structures, with brain regions as nodes and their connections as edges and apply Graph Neural Networks (GNNs) for classification. The GNN-based model outperformed traditional approaches in most cases, achieving the highest AUC of 0.86 in binary classification between healthy controls and bipolar disorder. These findings demonstrate the potential of GNNs for advancing the understanding and diagnosis of psychiatric conditions.

## Object
Objective of this study is to preserve both spatial and connectivity information while enhancing the interpretability of the analysis for improved understanding and diagnosis of major psychiatric disorders.

## Process
<img src="https://github.com/user-attachments/assets/f2b3adf9-9130-45aa-8977-12205bc9fa28" width="700">

## Pre-processing
### Data Transformation
- Tabular to Graph
  - Node Definition : Brain regions were defined as nodes within the graph structure, resulting in a total of 20 nodes (10 from each hemisphere).
  - Edge Definition : The connections between these brain regions were represented as edges, yielding a total of 190 edges based on EEG connectivity.
- Frequency to Wave
  - Delta Waves (1–3 Hz), Theta Waves (4–8 Hz), Alpha Waves (9–13 Hz), Beta Waves (14–30 Hz), Gamma Waves (31–40 Hz)
### Edge Selection
- Hotelling’s t-test
  - Hotelling’s t-test was used to handle multivariate data (connectivity values across 5 frequency bands.
  - Multiple correction was used to control multiple comparisons across 190 edges. Three correction method were tested.
    - Bonferroni correction, Benjamini-Hochberg (BH) adjustment, Benjamini-Yekutieli (BY) adjustment
  - graph example
    
    <img src="https://github.com/user-attachments/assets/bf9a2cf6-3c04-4d14-b779-00d80374915e" width="700">


- Threshold
  - Edges were filtered based on their EEG connectivity values.
  - Edges with values below the threshold were assigned a value of zero. If all frequency bands for a specific edge fell below the threshold, the connection was entirely removed from the graph.
  - Three threshold values (40, 45, and 50) were tested.
  - graph example
    
    <img src="https://github.com/user-attachments/assets/1fda3526-66e4-44c1-a2e8-a14198e8c546" width="700">



## Modeling
### Model Evaluation Using AUC
<img src="https://github.com/user-attachments/assets/4c898d98-dc2d-4887-b5e6-dbd92a8aa877" width="700">

