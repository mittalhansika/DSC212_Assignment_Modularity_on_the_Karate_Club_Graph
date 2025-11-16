# DSC_212_Assignment_Modularity_on_the_Karate_Club_Graph_by_Hansika_Mittal_IMS24287
Implementation of recursive spectral modularity to detect communities in the Wayne W. Zachary's Karate Club network, including visualisations and node-metric analysis.

------------------------------
__Name__: Hansika Mittal  
__Roll no.__: IMS24287  
__Batch__: BS-MS 2024  
__Course__: DSC212 Mathematical Foundations to Data Science  
__Course Instructor__: Dr. Saptarshi Bej  

-------------------------------
## Recursive Spectral Modularity - Karate Club Graph 
This project applies __recursive spectral modularity__ to identify communities in __Zachary's Karate Club__ network. The method follows Newman's approach, where communities are identified by splitting the graph according to the leading eigenvector of the modularity matrix. The algorithm continues splitting until no further improvement in modularity is possible, or when two consecutive iterations produce the same partition. This prevents unnecessary recursion and provides a natural stopping point.

----------------------------------
## Overview
Spectral modularity is a community detection method that uses the eigenvalues and eigenvectors of the __modularity matrix__ to determine meaningful divisions within a network. In this project:
1. The Karate Club graph is loaded using NetworkX.
2. The modularity matrix is computed for the current community.
3. The graph is split into two groups according to the sign of the leading eigenvector.
4. Each resulting subgraph is tested to see if further splitting improves modularity.
5. The process repeats recursively across communities.
6. The loop ends automatically once two consecutive iterations produce the __same partition__, indicating convergence.

At each iteration, node-level metrics are recorded: Degree centrality, Betweenness centrality, Closeness centrality, Clustering coefficient and evolving structure is visualized. This makes it easy to study how community formation influences node importance over time.

----------------------
## Installation 
Installing the required packages:  
```pip install networkx numpy pandas matplotlib```

-------------------
## Findings
The algorithm converged to three stable communities.

Community 1
Nodes: 0, 1, 2, 3, 7, 11, 12, 13, 17, 19, 21
This group contains several core members around node 0, reflecting a tightly interconnected cluster with consistently high centrality values.

Community 2
Nodes: 4, 5, 6, 10, 16
A small, cohesive subgroup with high local clustering, which explains why modularity treats it as an independent community.

Community 3
Nodes: 8, 9, 14, 15, 18, 20, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31
This is the largest and most diffuse cluster, centered around node 33’s side of the traditional split. Several bridging nodes maintain moderate betweenness before the structure stabilizes.

Centrality rankings stabilize once these three groups form, indicating that no further modularity-increasing splits were possible.

The presence of a third community highlights a meaningful intermediate subgroup that spectral modularity is sensitive enough to detect, even though traditional treatments often show only two factions.

---------------------
## Background  
This project follows the modularity-maximization framework developed by:  
__Newman, M. E. J. (2006)__
"Modularity and community structure in networks", PNAS 103(23):8577–8582.  
Zachary's Karate Club network is a classical dataset used for validating community detection methods.

