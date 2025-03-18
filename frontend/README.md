# Frontend Documentation

## Overview
The frontend component provides an interactive web interface for the stock prediction system, featuring real-time data visualization and user controls.

## Directory Structure
```
frontend/
├── public/           # Static assets
└── src/             # Source code
    ├── components/  # React components
    ├── pages/       # Page components
    ├── services/    # API services
    ├── utils/       # Utility functions
    └── styles/      # CSS styles
```

## Features

### 1. Interactive Dashboard
- Real-time stock price charts
- Technical indicators visualization
- Prediction results display
- Portfolio management interface

### 2. Data Visualization
- Candlestick charts
- Line graphs
- Volume analysis
- Technical indicator overlays

### 3. User Interface Components
- Stock search and selection
- Time period selection
- Model parameter configuration
- Alert settings

## Technologies Used
- React.js
- TypeScript
- Chart.js
- Material-UI
- Axios for API calls

## Setup
1. Install dependencies:
   ```bash
   npm install
   ```

2. Start development server:
   ```bash
   npm start
   ```

3. Build for production:
   ```bash
   npm run build
   ```

## Component Documentation

### Main Components
- `Dashboard`: Main application interface
- `StockChart`: Interactive price chart
- `PredictionPanel`: Model predictions display
- `TechnicalIndicators`: Technical analysis tools
- `PortfolioManager`: Portfolio tracking interface

### API Integration
- Real-time data updates
- WebSocket connections for live prices
- RESTful API calls for predictions
- Historical data fetching 