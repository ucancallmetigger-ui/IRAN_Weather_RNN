# IRAN_Weather_RNN
If you look for Temperature forecasting system utilizing RNNs and more advance models such as LSTM and GRU, This project be usefull for sure.

This project implements a complete temperature forecasting system for major cities in Iran (Tehran, Isfahan, Shiraz, Tabriz, Mashhad). It fetches real-time historical and forecast data directly from the Open-Meteo API without requiring any pre-downloaded dataset.
The main goal is to compare classical statistical baselines with deep learning models for time series forecasting, where all recurrent architectures are implemented from scratch using pure PyTorch (no high-level nn.LSTM or nn.GRU modules).
key-features:
 Fully online data pipline
 Multi-city spatio-temporal modeling
 Custom recurrent cells with detailed ablation study
 Comprehensive model comparison (accuracy, stability, computational cost)
 Interactive web dashboard built with Streamlit



 Advanced models implemented from scratch:
 
Custom LSTM 

Custom GRU

ConvLSTM for spatial-temporal patterns across cities

Temporal Convolutional Network

Transformer encoder for time series

LISENCE:
 This project is licensed under the MIT License - see the LICENSE file for details.
