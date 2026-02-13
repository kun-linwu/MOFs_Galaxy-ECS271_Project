# Predicting Guest Molecule Accessibility in Metal-Organic Frameworks (MOFs)

This project develops a Graph Convolutional Network (GCN) framework to predict guest molecule accessibility in Metal-Organic Frameworks (MOFs) based on Pore Limiting Diameter (PLD) ranges. By treating MOFs as nodes in a social network, we aim to overcome the computational complexity of traditional screening tools like ZEO++. Our investigation compares multiple architectures, which are MLP, GCN, and GraphSAGE, to enhance high-throughput screening efficiency for gas adsorption and separation applications.

## Technical Skills Used
- **Graph Neural Networks (GNNs)**: Implementation of GCN and GraphSAGE architectures to capture structural patterns in graph-structured data.
- **Machine Learning Pipelines**: Development of a baseline Multi-layer Perceptron (MLP) for performance benchmarking.
- **Hyperparameter Optimization**: Systematic model tuning using Optuna to optimize hidden layers, neurons, dropout, and learning rates.
- **Data Science & NLP**: Cleaning SMILES strings, generating Morgan Fingerprints, and utilizing Tanimoto similarity for structural relationship modeling.
- **Dimensionality Reduction**: Visualizing high-dimensional node embeddings through t-SNE to analyze class clustering.
- **Network Analysis**: Using Gephi and the OpenOrd layout to visualize the "MOFGalaxyNet" similarity network.

## Features
This repository provides a refined dataset of 1,988 MOFs, curated and cleaned from the MOFGalaxyNet study to correct errors in original SMILES strings. Each MOF is represented by seven key features, including atomic properties and organic ligand fingerprints, which are normalized and vectorized for model input.

The project features a comparative analysis across three distinct model types: a baseline MLP, a standard GCN for structural capture, and GraphSAGE for inductive learning on unseen data. Additionally, we provide the optimized hyperparameter sets identified via Optuna, which achieved approximately 70% validation accuracy across all models.

## The Process
The workflow began with data preparation, where we calculated cosine and Tanimoto similarities between MOF pairs based on their physical properties and Morgan Fingerprints. We then constructed an adjacency matrix by applying a 0.9 pruning threshold to establish a robust similarity-based graph network called MOFGalaxyNet.

Following data curation, we conducted sequential hyperparameter studies. The first study focused on architectural tuning (hidden layers and neurons), while the second refined learning parameters like batch size and learning rate. Finally, we analyzed the models using confusion matrices and t-SNE visualizations to understand how the models learned node embeddings and where class overlaps occurred.

## What I've Learned
Through this project, I gained a deep understanding of the strengths and limitations of graph-based models compared to standard deep learning. While we expected GCN and GraphSAGE to significantly outperform the MLP baseline, our results showed only marginal improvements. This taught me the importance of input feature quality and how "overlapping" data points in the embedding space can bottleneck model accuracy.

I also learned how to translate chemical design spaces into social network contexts, providing a more intuitive way to view material relationships. Managing the computational trade-offs between neighborhood sampling in GraphSAGE and layer-wise propagation in GCNs provided practical experience in scaling GNNs for scientific discovery.

## Future Improvements
- Advanced Architectures: Implement Graph Attention Networks (GAT) to allow the model to learn the relative importance of neighboring MOFs.
- CIF-Based Graph Construction: Construct graph structures for each individual MOF directly from its Crystallographic Information File (CIF) rather than a similarity network.
- Feature Engineering: Improve input feature quality by incorporating more granular 3-D structural descriptors.
- Extended Property Prediction: Apply the framework to predict other critical properties such as thermal stability and methane storage capacity.

## MOFGalaxyNet Visualization
<img width="667" height="651" alt="Gephi_1988_OpenOrd" src="https://github.com/user-attachments/assets/42b50423-c556-46e6-8004-8201a72d3b56" />

(Refer to Figure 1 in the project report for the Gephi visualization)
