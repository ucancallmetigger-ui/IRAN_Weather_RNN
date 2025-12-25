# IRAN_Weather_RNN
Iran Weather Forecasting with Deep Learning & Time-Series Models

This project presents a comprehensive weather forecasting system for major Iranian cities, combining classical statistical models, custom-built deep learning architectures, and an interactive Streamlit dashboard for real-time analysis and comparison.

The system focuses on daily mean temperature prediction using historical meteorological data and evaluates multiple modeling paradigms in terms of accuracy, stability, training efficiency, and memory usage.


"Covered Cities"

The project analyzes and forecasts weather data for the following cities:

1-Tehran

2-Isfahan

3-Shiraz

4-Tabriz

5-Mashhad

Each city is defined using precise geographical coordinates and processed independently and jointly (spatio-temporal modeling).


"Data Source & Collection"

Weather data is retrieved dynamically from the Open-Meteo API, including:

Historical daily mean temperature data

Official short-term forecast data for validation

Date range: 2010 → Present

To optimize performance, data fetching is cached using Streamlit’s caching mechanism.

"Data Preprocessing"

Key preprocessing steps include:

1-Missing-value handling via forward filling

2-Feature scaling using MinMaxScaler

3-Sliding window sequence generation (default: 30 days)

4-City-wise normalization for spatial modeling

5-Two preprocessing pipelines are implemented:

6-Univariate temporal sequences

7-Multi-city spatial–temporal tensors

"Modeling Approaches"

The project performs an extensive comparison between statistical, machine learning, and deep learning models.

"Baseline & Statistical Models"

1-Moving Average

2-Linear Regression

3-ARIMA

4-These models serve as interpretable baselines for evaluating deep learning gains.

5-Custom Recurrent Neural Networks (From Scratch)

All recurrent models are implemented without relying on high-level PyTorch abstractions, enabling full control and interpretability.

"Custom LSTM"

-Manual gate definitions (input, forget, output, candidate)

-Multi-layer architecture

-Gradient clipping for stability

-Ablation Study

To analyze gate importance, three ablation variants are implemented:

-No Forget Gate

-No Input Gate

-No Output Gate

>>>This provides insight into how each gate contributes to long-term dependency modeling.

"Custom GRU"

-Fully manual GRU cell implementation

-Multi-layer recurrent processing

-Efficient alternative to LSTM              

-Advanced Deep Learning Models

"ConvLSTM"

-Captures spatial correlations between cities using convolutional recurrence.

-Temporal CNN

-Learns temporal patterns using stacked 1D convolutions.

"Time-Series Transformer"

Uses self-attention mechanisms with positional encoding for long-range dependency modeling.

-Training Configuration

-Optimizer: Adam

-Loss Function: Mean Squared Error (MSE)

-Learning Rate Scheduler: ReduceLROnPlateau

-Epochs: Configurable (default: 50)

-Device: CPU / CUDA (auto-detected)

-Additional training diagnostics:

-Gradient norm tracking

-Training time measurement

-Memory usage monitoring

"Evaluation Metrics"

Each model is evaluated using:

1-RMSE (Root Mean Squared Error)

2-MAE (Mean Absolute Error)

3-Training Stability (loss variance)

4-Training Time

5-Memory Consumption

Results are presented in a comparative table directly inside the Streamlit interface.

"Visualization & Analysis"

The dashboard provides:

1-Model comparison tables

2-Gradient norm plots for LSTM & GRU

3-7-day temperature forecasts

4-Comparison with official meteorological forecasts

5-Ablation study summaries

All plots are rendered interactively using Matplotlib + Streamlit.

"Interactive Dashboard (Streamlit)"

The application allows users to:

1-Select a city dynamically

2-Train and evaluate multiple models

3-Visualize predictions and official forecasts

4-Compare performance metrics in real time

5-Designed for research demos, educational use, and portfolio showcasing.

"Technologies Used"

1-Python

2-PyTorch

3-Streamlit

4-Statsmodels

5-Scikit-learn

6-Matplotlib & Seaborn

7-Open-Meteo API
