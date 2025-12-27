# Seattle Marriott Bellevue - Customer Support Chatbot Demo

A simple chatbot demo for hotel customer support, powered by Google Gemini.

## Features

- Answer questions about the hotel, amenities, and local area
- Check-in assistance
- Check-out processing
- Room service orders
- Guest feedback and complaint handling

## Local Setup

### 1. Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On macOS/Linux
# or
venv\Scripts\activate     # On Windows
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure Gemini API Key

Create a `.env` file in the project root:

```
GEMINI_API_KEY=your_gemini_api_key_here
```

Get your API key from: https://aistudio.google.com/apikey

### 4. Run the Server

```bash
python main.py
```

Or with uvicorn directly:

```bash
uvicorn main:app --reload
```

### 5. Open the Chat

Visit: http://localhost:8000

---

## Deploy to Koyeb (Free, Always Running)

Koyeb keeps your app running 24/7 with no cold starts.

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/marriott-chatbot.git
git push -u origin main
```

### 2. Create Koyeb Account

Go to https://www.koyeb.com and sign up (free, no credit card required).

### 3. Deploy

1. Click "Create App"
2. Select "GitHub" and connect your repository
3. Configure:
   - Name: `marriott-chatbot`
   - Builder: `Buildpack`
   - Run command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
   - Instance type: `Free`

4. Add Environment Variable:
   - Key: `GEMINI_API_KEY`
   - Value: Your Gemini API key

5. Click "Deploy"

### 4. Access Your Chatbot

Your chatbot will be live at:
```
https://marriott-chatbot-YOUR_USERNAME.koyeb.app
```

No cold starts - always responds instantly!

---

## Project Structure

```
deca/
├── main.py          # FastAPI server + chat logic
├── index.html       # Chat UI
├── requirements.txt # Python dependencies
├── Procfile         # Koyeb deployment config
├── .env             # Your Gemini API key (local only)
└── README.md        # This file
```

## API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Serves the chat UI |
| `/chat` | POST | Send a message, get AI response |
| `/reset` | POST | Reset conversation history |
| `/health` | GET | Health check |

## Usage Example

```bash
curl -X POST http://localhost:8000/chat \
  -H "Content-Type: application/json" \
  -d '{"message": "What time is checkout?", "session_id": "test"}'
```
