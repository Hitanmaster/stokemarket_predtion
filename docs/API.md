# API Documentation

## Authentication
All API endpoints require JWT authentication. Include the token in the Authorization header:
```
Authorization: Bearer <your_jwt_token>
```

## Endpoints

### Stock Data Endpoints

#### Get Current Stock Data
```http
GET /api/stock/:symbol
```

**Parameters:**
- `symbol` (path): Stock symbol (e.g., AAPL, GOOGL)

**Response:**
```json
{
  "symbol": "AAPL",
  "price": 150.25,
  "change": 2.5,
  "change_percent": 1.67,
  "volume": 75000000,
  "timestamp": "2024-03-15T10:30:00Z"
}
```

#### Get Historical Data
```http
GET /api/stock/:symbol/history
```

**Query Parameters:**
- `start_date`: Start date (YYYY-MM-DD)
- `end_date`: End date (YYYY-MM-DD)
- `interval`: Data interval (1m, 5m, 15m, 1h, 1d)

**Response:**
```json
{
  "symbol": "AAPL",
  "data": [
    {
      "timestamp": "2024-03-15T10:30:00Z",
      "open": 150.00,
      "high": 151.00,
      "low": 149.50,
      "close": 150.25,
      "volume": 75000000
    }
  ]
}
```

### Model Endpoints

#### Train Model
```http
POST /api/model/train
```

**Request Body:**
```json
{
  "symbol": "AAPL",
  "parameters": {
    "window_size": 60,
    "features": ["price", "volume", "rsi", "macd"],
    "target": "close_price"
  }
}
```

**Response:**
```json
{
  "status": "success",
  "model_id": "model_123",
  "training_started": "2024-03-15T10:30:00Z"
}
```

#### Get Model Status
```http
GET /api/model/status/:model_id
```

**Response:**
```json
{
  "model_id": "model_123",
  "status": "training",
  "progress": 75,
  "metrics": {
    "mae": 2.5,
    "rmse": 3.1,
    "r2": 0.85
  }
}
```

#### Make Prediction
```http
POST /api/model/predict
```

**Request Body:**
```json
{
  "model_id": "model_123",
  "data": {
    "window_size": 60,
    "features": [...]
  }
}
```

**Response:**
```json
{
  "prediction": 152.50,
  "confidence": 0.85,
  "timestamp": "2024-03-15T10:30:00Z"
}
```

## Error Responses

### 400 Bad Request
```json
{
  "error": "Invalid parameters",
  "details": "Invalid date format"
}
```

### 401 Unauthorized
```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing authentication token"
}
```

### 404 Not Found
```json
{
  "error": "Not Found",
  "message": "Stock symbol not found"
}
```

### 500 Internal Server Error
```json
{
  "error": "Internal Server Error",
  "message": "An unexpected error occurred"
}
``` 