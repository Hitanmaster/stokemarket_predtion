# Development Setup Guide

## Prerequisites

### System Requirements
- Node.js 16.x or higher
- Python 3.8 or higher
- Git
- PostgreSQL 13.x or higher
- Redis (for caching and WebSocket)

### Development Tools
- VS Code (recommended)
- Chrome DevTools
- Postman (for API testing)

## Environment Setup

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/stock-prediction.git
cd stock-prediction
```

### 2. Backend Setup

#### Create Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

#### Install Dependencies
```bash
cd backend
pip install -r requirements.txt
```

#### Environment Variables
Create `.env` file in the backend directory:
```env
DATABASE_URL=postgresql://user:password@localhost:5432/stockdb
REDIS_URL=redis://localhost:6379
JWT_SECRET=your_jwt_secret
API_KEY=your_stock_api_key
```

#### Database Setup
```bash
# Create database
createdb stockdb

# Run migrations
python manage.py migrate
```

### 3. Frontend Setup

#### Install Dependencies
```bash
cd frontend
npm install
```

#### Environment Variables
Create `.env` file in the frontend directory:
```env
REACT_APP_API_URL=http://localhost:8000
REACT_APP_WS_URL=ws://localhost:8000
```

## Running the Application

### Development Mode

1. Start Backend Server:
```bash
cd backend
python manage.py runserver
```

2. Start Frontend Development Server:
```bash
cd frontend
npm start
```

3. Start Redis Server:
```bash
redis-server
```

### Production Mode

1. Build Frontend:
```bash
cd frontend
npm run build
```

2. Start Production Server:
```bash
cd backend
gunicorn app:app
```

## Testing

### Backend Tests
```bash
cd backend
pytest
```

### Frontend Tests
```bash
cd frontend
npm test
```

## Code Quality Tools

### Backend
- Black for code formatting
- Flake8 for linting
- MyPy for type checking

```bash
# Format code
black .

# Run linter
flake8

# Type checking
mypy .
```

### Frontend
- ESLint for linting
- Prettier for code formatting
- TypeScript for type checking

```bash
# Format code
npm run format

# Run linter
npm run lint

# Type checking
npm run type-check
```

## Git Workflow

1. Create feature branch:
```bash
git checkout -b feature/your-feature
```

2. Make changes and commit:
```bash
git add .
git commit -m "feat: your feature description"
```

3. Push changes:
```bash
git push origin feature/your-feature
```

4. Create pull request on GitHub

## Deployment

### Backend Deployment
1. Set up production environment variables
2. Configure database
3. Set up SSL certificates
4. Deploy using Docker or cloud platform

### Frontend Deployment
1. Build production assets
2. Deploy to CDN or static hosting
3. Configure environment variables
4. Set up CI/CD pipeline

## Monitoring and Logging

### Backend Logging
- Configure logging in `config.py`
- Set up log rotation
- Monitor application metrics

### Frontend Monitoring
- Set up error tracking
- Configure performance monitoring
- Implement analytics

## Security Best Practices

1. **Authentication**
   - Use JWT tokens
   - Implement refresh tokens
   - Set secure cookie options

2. **API Security**
   - Rate limiting
   - Input validation
   - CORS configuration

3. **Data Security**
   - Encrypt sensitive data
   - Use prepared statements
   - Implement data backup

4. **Infrastructure Security**
   - Regular security updates
   - Firewall configuration
   - SSL/TLS setup 