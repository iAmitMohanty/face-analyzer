# Skin Analyzer - AI-Powered Skin Analysis

A comprehensive skin analysis application built with React frontend and Python Flask backend, featuring MediaPipe face analysis and GPT-4o powered recommendations.

## Features

- **AI Skin Analysis**: Analyze skin conditions using MediaPipe face detection and mesh analysis
- **Advanced Skin Concern Detection**: Identify breakouts, pigmentation, redness, aging, dehydration, and under-eye concerns
- **GPT-4o Powered Recommendations**: Get personalized ingredient suggestions and skincare advice
- **Fallback Mode**: Works without OpenAI API key using simulated analysis
- **Modern UI**: Beautiful, responsive interface with drag-and-drop image upload
- **Real-time Analysis**: Instant skin analysis with detailed results and confidence scores
- **Comprehensive Results**: Detailed breakdown of skin concerns with severity levels

## Tech Stack

### Frontend
- React 18 with TypeScript
- Tailwind CSS for styling
- React Router for navigation
- React Dropzone for file uploads
- Heroicons for UI icons
- Axios for API communication

### Backend
- Python Flask with CORS support
- MediaPipe for advanced face detection and mesh analysis
- OpenAI GPT-4o for intelligent recommendations
- OpenCV for image processing
- NumPy for mathematical calculations
- PIL (Pillow) for image handling
- Gunicorn for production deployment

## Installation

### Quick Setup (Linux/macOS)
```bash
# Make setup script executable and run
chmod +x setup.sh
./setup.sh
```

### Manual Setup

#### Backend Setup
```bash
cd backend
python -m venv venv
venv\Scripts\activate  # On Windows
# source venv/bin/activate  # On macOS/Linux
pip install -r requirements.txt
copy env.example .env  # On Windows
# cp env.example .env  # On macOS/Linux
python app.py
```

#### Frontend Setup
```bash
cd frontend
npm install
copy env.example .env  # On Windows
# cp env.example .env  # On macOS/Linux
npm start
```

## Environment Variables

### Backend (.env)
Create a `.env` file in the backend directory:
```
# OpenAI API Configuration
OPENAI_API_KEY=your_openai_api_key_here

# Flask Configuration
FLASK_ENV=development
FLASK_DEBUG=True
PORT=5000

# Optional: Logging Configuration
# LOG_LEVEL=INFO
```

### Frontend (.env)
Create a `.env` file in the frontend directory:
```
# API Configuration
REACT_APP_API_URL=http://localhost:5000/api

# Optional: Environment Configuration
REACT_APP_ENV=development
```

**Important:** You need an OpenAI API key for full functionality. Get one from [OpenAI Platform](https://platform.openai.com/api-keys).

## Usage

1. Start the backend server (runs on http://localhost:5000)
2. Start the frontend development server (runs on http://localhost:3000)
3. Navigate to the application in your browser
4. Upload a photo for skin analysis using drag-and-drop or file selection
5. View detailed analysis results with confidence scores
6. Get personalized recommendations based on detected skin concerns

## API Endpoints

- `GET /api/health`: Health check endpoint
- `POST /api/analyze-skin`: Upload and analyze skin image
- `POST /api/recommendations`: Get personalized recommendations based on analysis
- `POST /api/test-fallback`: Test fallback mode functionality
- `GET /api/ingredients`: Get ingredient recommendations

## Project Structure

```
face-analyzer/
├── backend/
│   ├── app.py                 # Main Flask application
│   ├── skin_analyzer.py       # MediaPipe skin analysis logic
│   ├── gpt_recommendations.py # GPT-4o recommendation engine
│   ├── logger_utils.py        # Logging utilities
│   ├── test_analysis.py       # Analysis testing utilities
│   ├── requirements.txt       # Python dependencies
│   ├── env.example           # Environment variables template
│   └── venv/                 # Python virtual environment
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   │   └── Header.tsx    # Navigation header
│   │   ├── pages/
│   │   │   ├── HomePage.tsx      # Landing page
│   │   │   ├── AnalysisPage.tsx  # Image upload and analysis
│   │   │   ├── ResultsPage.tsx   # Analysis results display
│   │   │   ├── IngredientsPage.tsx # Ingredient recommendations
│   │   │   └── AboutPage.tsx     # About page
│   │   ├── services/
│   │   │   └── api.ts        # API communication
│   │   ├── types/
│   │   │   └── index.ts      # TypeScript type definitions
│   │   ├── App.tsx           # Main React component
│   │   └── index.tsx         # React entry point
│   ├── package.json          # Node.js dependencies
│   ├── tailwind.config.js    # Tailwind CSS configuration
│   └── env.example          # Frontend environment variables
├── logs/
│   └── applog.log           # Application logs
├── setup.sh                 # Automated setup script
├── DOCUMENTATION.md         # Detailed documentation
└── README.md               # This file
```

## Troubleshooting

### Common Issues

**Backend won't start:**
- Make sure you're in the virtual environment: `venv\Scripts\activate` (Windows) or `source venv/bin/activate` (macOS/Linux)
- Check that all dependencies are installed: `pip install -r requirements.txt`
- Verify your `.env` file exists and has the correct format
- Check the logs in `logs/applog.log` for detailed error messages

**Frontend won't start:**
- Make sure Node.js is installed: `node --version`
- Install dependencies: `npm install`
- Check that the `.env` file exists in the frontend directory
- Clear npm cache if needed: `npm cache clean --force`

**Analysis fails:**
- Ensure your OpenAI API key is set correctly in `backend/.env`
- Check that the image is clear and shows a face
- Verify the backend is running on port 5000
- Check browser console and backend logs for error details

**API connection errors:**
- Make sure both backend and frontend are running
- Check that `REACT_APP_API_URL` is set correctly in `frontend/.env`
- Verify CORS is enabled (should be automatic)
- Test the health endpoint: `http://localhost:5000/api/health`

**Face detection issues:**
- Ensure the image shows a clear, well-lit face
- Avoid heavy makeup or accessories that obscure facial features
- Try taking a photo from chest level showing your full face
- The system can handle partial faces but with limited analysis

### Fallback Mode

If you don't have an OpenAI API key, the application will run in fallback mode:
- Skin analysis will use simulated results based on image processing
- Recommendations will be generic but still helpful
- All other features will work normally
- You can test fallback mode using the `/api/test-fallback` endpoint

## Development

### Running Tests
```bash
# Backend tests
cd backend
python test_analysis.py

# Frontend tests
cd frontend
npm test
```

### Building for Production
```bash
# Frontend build
cd frontend
npm run build

# Backend with Gunicorn
cd backend
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the LICENSE file for details. 
