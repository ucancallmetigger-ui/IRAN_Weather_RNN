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

Effective preprocessing is critical for time-series forecasting, especially when using deep learning models. This project applies several preprocessing techniques, each serving a specific purpose.

Key preprocessing steps include:

1-Missing-value handling via forward filling

Missing Value Handling (Forward Fill):

Missing temperature values are handled using forward filling, ensuring temporal continuity.

-Why it matters:
Prevents sequence breaks that could disrupt recurrent learning while preserving realistic temporal behavior.

2-Feature scaling using MinMaxScaler

Feature Scaling (Min–Max Normalization):

All temperature values are normalized to the range [0, 1].

-Why it matters:

>Stabilizes gradient updates

>Accelerates model convergence

>Prevents domination of large numerical values

3-Sliding window sequence generation (default: 30 days)

Sliding Window Sequence Generation:

Time-series data is transformed into overlapping sequences of fixed length (default: 30 days).

-Why it matters:

>Enables supervised learning from sequential data

>Allows models to learn temporal dependencies

>Defines the effective “memory horizon” of the model

4-City-wise normalization for spatial modeling

Spatial–Temporal Preprocessing:

For multi-city modeling, each city’s data is scaled independently and combined into a unified tensor.

-Why it matters:

>Preserves local city-specific distributions

>Enables spatial correlation learning

>Supports ConvLSTM-based architectures

"These preprocessing steps directly influence model stability, convergence speed, and prediction accuracy, forming the backbone of the entire forecasting pipeline."

-Two preprocessing pipelines are implemented:

1-Univariate temporal sequences

2-Multi-city spatial–temporal tensors

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

-Custom LSTM – Model Explanation & Advantages over RNNs

The Custom LSTM implemented in this project is a manually constructed recurrent neural network designed to overcome the limitations of standard RNNs when modeling long time-series data.

>>>How It Works

Unlike vanilla RNNs, which rely on a single hidden state, LSTM introduces a memory cell that runs through time with controlled information flow via gates. This design allows the network to:

1-Preserve long-term contextual information

2-Selectively update or forget memory contents

3-Mitigate vanishing and exploding gradient problems

>>>Why LSTM Over RNN?

Standard RNNs struggle with long sequences due to unstable gradients, causing them to focus mostly on short-term dependencies.

LSTM advantages include:

Stable gradient propagation over long sequences

Explicit memory control through gating mechanisms

Superior performance on long-horizon forecasting tasks such as climate and weather data

In this project, LSTM significantly outperforms vanilla sequence models by capturing both seasonal patterns and gradual temperature trends.

and the other advantages are:

-Manual gate definitions (input, forget, output, candidate)

-Multi-layer architecture

-Gradient clipping for stability

-Ablation Study

>>>LSTM Ablation Study – Gate-Level Analysis

In order to better understand the internal dynamics of the LSTM architecture, an ablation study is conducted by selectively disabling individual gates. This analysis highlights the functional importance of each gate in modeling long-term temporal dependencies.

-Forget Gate

The forget gate controls how much of the previous cell state is retained over time.
It enables the model to selectively discard irrelevant or outdated information.

Impact:
Without the forget gate, the model accumulates unnecessary historical information, leading to unstable learning and degraded long-term forecasting performance.

-Input Gate

The input gate determines how much new information is written into the cell state at each time step.

Impact:
Removing the input gate restricts the model’s ability to adapt to new patterns or sudden changes in temperature trends, reducing responsiveness to recent data.

-Output Gate

The output gate controls how much of the internal cell state is exposed to the hidden state and downstream layers.

Impact:
Disabling the output gate limits the model’s expressive power, as relevant internal memory cannot be effectively propagated to predictions.


>>>The ablation study demonstrates that all three gates play complementary roles. The forget gate is particularly critical for long-term stability, while the input and output gates govern adaptability and expressiveness.

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
