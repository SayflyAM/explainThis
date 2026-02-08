# ExplainThis

**AI-powered Arabic & English text simplification using FastAPI, React, and NLP models.**

ExplainThis is a web application that takes complex text in either Arabic or English and produces a simplified, easy-to-understand version. It uses Hugging Face NLP models to power the text simplification pipeline.

## Project Structure

This project uses a **monorepo** layout:

```
explainThis/
├── backend/        # FastAPI Python backend
│   ├── main.py             # Application entry point
│   └── requirements.txt    # Python dependencies
├── frontend/       # React (Vite) frontend
│   ├── src/                # React source code
│   ├── package.json        # Node.js dependencies
│   └── vite.config.js      # Vite configuration
├── .gitignore
└── README.md
```

## Features

- **Bilingual Support:** Automatically detects Arabic and English input text.
- **Text Simplification:** Uses NLP models to simplify complex text.
- **Simple UI:** Clean, user-friendly interface for submitting text and viewing results.
- **Privacy-First:** No user data is stored locally or on the server.

## Quality Goals

| Priority | Goal           | Description                                                  |
|----------|----------------|--------------------------------------------------------------|
| 1        | Usability      | Simple, intuitive interface for all users                    |
| 2        | Performance    | Reasonable response times (under 5–10 seconds per paragraph) |
| 3        | Maintainability| Clean, modular code that's easy to extend                    |

## Getting Started

### Prerequisites

- **Python 3.10+** for the backend
- **Node.js 18+** and **npm** for the frontend

### Backend Setup

```bash
cd backend
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```

The API server will be available at `http://localhost:8000`.

### Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

The development server will be available at `http://localhost:5173`.

## API Endpoints

| Method | Endpoint       | Description                        |
|--------|----------------|------------------------------------|
| GET    | `/`            | Health check / welcome message     |
| POST   | `/explain`     | Submit text for simplification     |

## NLP Models

| Language | Model (Planned)                        |
|----------|----------------------------------------|
| English  | BART-large-cnn or T5 variant           |
| Arabic   | AraBART or AraT5                       |

## Architecture

The application follows a layered architecture:

1. **Request Validator** – Validates input text (non-empty, within character limits).
2. **Language Detector** – Detects whether the input is Arabic or English.
3. **Model Router** – Selects the correct NLP model based on detected language.
4. **NLP Client** – Runs the selected model to generate simplified text.
5. **Response Formatter** – Returns structured JSON to the frontend.

## License

This project is for educational purposes.
