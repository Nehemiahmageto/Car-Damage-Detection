AI-Based Damage Severity Assessment Using Computer Vision and Hybrid Machine Learning
1. Project Overview

This project aims to build an end-to-end AI-driven damage assessment system that goes beyond simple image classification. Instead of only detecting whether damage exists, the system estimates damage severity by combining computer vision, temporal modeling, and structured machine learning.

The core idea is simple but powerful: images show damage, time shows progression, and tabular data provides context. By integrating these perspectives, the model produces severity scores that are meaningful for real-world decision-making such as insurance claim prioritization or disaster response planning.

2. Problem Statement

Current automated damage detection systems often fail in practice because they:

Treat damage as a binary outcome (damage vs no damage)

Ignore how damage evolves over time

Do not integrate contextual metadata (location, asset characteristics)

This project addresses these gaps by answering the following question:

How severe is the damage, how does it evolve, and how should it be prioritized?

3. Dataset Description

The project uses publicly available datasets focused on visual damage assessment:

Primary Dataset Options

Car Damage Detection Dataset (Kaggle) – annotated images of damaged vehicles for object detection and classification

xBD Building Damage Assessment Dataset – satellite images with pre- and post-disaster building damage labels

Data Modalities

Image data: raw images used for visual feature extraction

Temporal data: ordered image sequences (where available) to capture damage progression

Tabular metadata: contextual features such as location type, asset category, or event intensity

4. Methodology
4.1 Visual Feature Extraction (CNN)

A pre-trained Convolutional Neural Network (CNN) is used to extract high-level visual features from damage images. Transfer learning is applied to leverage learned representations from large-scale image datasets.

Output:

Dense feature embeddings representing visual damage patterns

4.2 Temporal Modeling (LSTM)

When sequential image data is available, an LSTM network is used to model how damage features change over time. This allows the system to capture damage progression rather than static snapshots.

Output:

Temporal embeddings summarizing damage evolution

4.3 Severity Prediction (XGBoost)

XGBoost is used as the final decision model due to its strong performance on structured data. It combines:

CNN-derived visual features

LSTM temporal outputs (if available)

Tabular metadata features

Output:

Damage severity score or category

5. Model Architecture (High-Level)

Input images → CNN feature extractor

Feature sequences → LSTM (optional, when temporal data exists)

Visual + temporal + tabular features → XGBoost

Final severity prediction

This hybrid architecture mirrors real-world AI systems where different models specialize in different types of information.

6. Evaluation Strategy

Models are evaluated using:

Classification metrics (accuracy, F1-score) for categorical severity

Regression metrics (RMSE, MAE) for severity scoring

Visual inspection of detection outputs

Error analysis on misclassified or ambiguous cases

Emphasis is placed on interpretability and failure analysis, not just raw performance.

7. Explainability and Insights

To ensure transparency:

SHAP values are used to explain XGBoost predictions

Feature importance analysis highlights key damage drivers

Visual outputs include bounding boxes and severity heatmaps

This ensures the system provides actionable insights, not just predictions.
