Beijing Air Quality Forecasting

This repository contains an end-to-end pipeline for forecasting PM2.5 concentrations in Beijing using historical weather and air quality data.
The project uses LSTM-based neural networks to capture temporal dependencies and generate accurate predictions suitable for Kaggle competitions.

Project Overview

Air pollution, specifically PM2.5, is a major public health issue.
This project builds a deep learning model to forecast PM2.5 concentrations based on weather features such as temperature, dew point, pressure, and wind speed.

Key Objectives:

Explore and visualize PM2.5 data trends.

Preprocess and scale input features.

Build and train an LSTM model.

Generate predictions and submit results to Kaggle.

Data

Training data: /train.csv

Test data: /test.csv

Features:

Weather Variables: DEWP, TEMP, PRES, Iws, Is, Ir

Wind Direction (One-Hot Encoded): cbwd_NW, cbwd_SE, cbwd_cv

Datetime Column: Converted to datetime type and set as index

Target Variable: pm2.5

Exploratory Data Analysis (EDA)

The notebook includes several visualizations:

Line Plot: PM2.5 concentration trends over time.

Histograms: Distributions of temperature, wind speed, and PM2.5.

Correlation Heatmap: Shows feature correlation (PM2.5 correlates strongly with DEWP, TEMP, PRES).

Preprocessing & Feature Engineering

Datetime Features: Extracted hour, dayofweek, month to capture temporal seasonality.

Scaling: Standardized all features using StandardScaler.

Sequence Preparation: Built sliding windows of 24 timesteps to predict the next hour's PM2.5.

Model Architecture

We implemented a stacked LSTM model:

Input: (24 timesteps × features)
↓
Bidirectional LSTM (128 units)
↓
Dropout (0.25)
↓
LSTM (64 units)
↓
Dropout (0.25)
↓
Dense (1)


Optimizer: Adam (lr=0.0005)

Loss Function: Mean Squared Error (MSE)

Callbacks: EarlyStopping & ReduceLROnPlateau to prevent overfitting

Kaggle Submission

After training, predictions were generated for the test set and saved in the exact format required by Kaggle

📂 Repository Structure
.
├── air_quality_forecasting.ipynb   # Main Notebook
├── train.csv                      # Training data
├── test.csv                       # Test data
├── sample_submission.csv          # Sample format
├── subm_fixed.csv                 # Final submission file
└── README.md                      # This file

🚀 How to Run

Clone this repository:

git clone https://github.com/your-username/air-quality-forecasting.git
cd air-quality-forecasting


Open the notebook in Google Colab or Jupyter:

jupyter notebook air_quality_forecasting.ipynb


Run all cells to reproduce results.
