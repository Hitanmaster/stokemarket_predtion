# Frontend Components Documentation

## Dashboard Component
```typescript
interface DashboardProps {
  initialSymbol?: string;
  timeRange?: TimeRange;
  onSymbolChange?: (symbol: string) => void;
}
```

**Purpose:** Main application interface displaying stock data and predictions.

**Usage:**
```tsx
<Dashboard 
  initialSymbol="AAPL"
  timeRange="1D"
  onSymbolChange={(symbol) => console.log(symbol)}
/>
```

**State Management:**
- Uses Redux for global state
- Local state for UI controls
- WebSocket for real-time updates

## StockChart Component
```typescript
interface StockChartProps {
  data: StockData[];
  indicators: TechnicalIndicator[];
  onTimeframeChange: (timeframe: Timeframe) => void;
}
```

**Purpose:** Interactive price chart with technical indicators.

**Usage:**
```tsx
<StockChart 
  data={stockData}
  indicators={['RSI', 'MACD']}
  onTimeframeChange={(tf) => setTimeframe(tf)}
/>
```

**Dependencies:**
- Chart.js
- react-chartjs-2
- date-fns

## PredictionPanel Component
```typescript
interface PredictionPanelProps {
  predictions: Prediction[];
  confidence: number;
  onRefresh: () => void;
}
```

**Purpose:** Displays model predictions and confidence metrics.

**Usage:**
```tsx
<PredictionPanel 
  predictions={modelPredictions}
  confidence={0.85}
  onRefresh={refreshPredictions}
/>
```

## TechnicalIndicators Component
```typescript
interface TechnicalIndicatorsProps {
  indicators: Indicator[];
  onIndicatorToggle: (indicator: string) => void;
}
```

**Purpose:** Technical analysis tools and indicators configuration.

**Usage:**
```tsx
<TechnicalIndicators 
  indicators={['RSI', 'MACD', 'BB']}
  onIndicatorToggle={(ind) => toggleIndicator(ind)}
/>
```

## PortfolioManager Component
```typescript
interface PortfolioManagerProps {
  portfolio: Portfolio;
  onTrade: (trade: Trade) => void;
}
```

**Purpose:** Portfolio tracking and management interface.

**Usage:**
```tsx
<PortfolioManager 
  portfolio={userPortfolio}
  onTrade={(trade) => executeTrade(trade)}
/>
```

## Common Types

```typescript
type TimeRange = '1D' | '1W' | '1M' | '3M' | '1Y' | 'ALL';
type Timeframe = '1m' | '5m' | '15m' | '1h' | '1d';

interface StockData {
  timestamp: string;
  open: number;
  high: number;
  low: number;
  close: number;
  volume: number;
}

interface Prediction {
  timestamp: string;
  price: number;
  confidence: number;
}

interface TechnicalIndicator {
  name: string;
  parameters: Record<string, number>;
  enabled: boolean;
}

interface Portfolio {
  holdings: Holding[];
  cash: number;
  totalValue: number;
}

interface Trade {
  symbol: string;
  type: 'BUY' | 'SELL';
  quantity: number;
  price: number;
}
```

## State Management

### Redux Store Structure
```typescript
interface RootState {
  stocks: {
    currentSymbol: string;
    data: StockData[];
    loading: boolean;
    error: string | null;
  };
  predictions: {
    data: Prediction[];
    loading: boolean;
    error: string | null;
  };
  portfolio: {
    holdings: Holding[];
    cash: number;
    loading: boolean;
    error: string | null;
  };
  ui: {
    selectedTimeframe: Timeframe;
    activeIndicators: string[];
    theme: 'light' | 'dark';
  };
}
```

## Error Handling

All components implement error boundaries and handle the following scenarios:
- API request failures
- WebSocket disconnections
- Invalid data formats
- Network timeouts

## Performance Optimization

1. **Memoization:**
   - Use React.memo for pure components
   - Implement useMemo for expensive calculations
   - Use useCallback for event handlers

2. **Lazy Loading:**
   - Implement code splitting for large components
   - Lazy load charts and heavy visualizations

3. **Data Management:**
   - Implement pagination for large datasets
   - Use virtualization for long lists
   - Cache API responses 