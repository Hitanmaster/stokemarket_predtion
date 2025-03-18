# Backend Documentation

## Overview
The backend component handles data processing, model training, and API endpoints for the stock prediction system.

## Directory Structure
```
backend/
├── api/              # API endpoints and routes
├── data_processing/  # Data preprocessing and cleaning
├── model/           # Machine learning models
├── utils/           # Utility functions
└── app/             # Application core logic
```

## Algorithms and Models

### 1. Data Processing
- Time series data normalization
- Feature engineering
- Technical indicators calculation
- Data cleaning and validation

### 2. Prediction Models
- LSTM (Long Short-Term Memory) neural network
- Random Forest regression
- XGBoost model
- Ensemble methods combining multiple models

### 3. Technical Indicators Used
- Moving Averages (SMA, EMA)
- RSI (Relative Strength Index)
- MACD (Moving Average Convergence Divergence)
- Bollinger Bands
- Volume indicators

## API Endpoints

### Stock Data
- `GET /api/stock/:symbol` - Get current stock data
- `GET /api/stock/:symbol/history` - Get historical data
- `GET /api/stock/:symbol/prediction` - Get price prediction

### Model Management
- `POST /api/model/train` - Train prediction model
- `GET /api/model/status` - Get model training status
- `POST /api/model/predict` - Make predictions

## Dependencies
- Python 3.8+
- TensorFlow
- scikit-learn
- pandas
- numpy
- FastAPI
- yfinance (for stock data)

## Setup
1. Create virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the server:
   ```bash
   python app.py
   ``` 