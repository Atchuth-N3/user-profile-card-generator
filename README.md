# User Profile Card Generator

An AI-powered web app where users input their details and get a beautifully formatted profile card. Built with **React** (frontend) and **Python Flask** (backend), powered by the **Anthropic Claude API**.

---

## Project Structure

```
user-profile-card-generator/
├── backend/
│   ├── app.py              # Flask API server
│   ├── requirements.txt    # Python dependencies
│   └── .env.example        # Environment variable template
└── frontend/
    ├── public/
    │   └── index.html
    ├── src/
    │   ├── components/
    │   │   ├── ProfileForm.js / .css
    │   │   └── ProfileCard.js / .css
    │   ├── App.js / .css
    │   └── index.js / .css
    └── package.json
```

---

## Quick Start

### Prerequisites

- **Node.js** v16+ and **npm** — https://nodejs.org
- **Python** 3.8+ — https://python.org
- An **Anthropic API key** — https://console.anthropic.com

---

### Step 1 — Set up the Backend

Open a terminal and run:

```bash
cd backend
pip install -r requirements.txt
```

Create your `.env` file:

```bash
# On Mac/Linux:
cp .env.example .env

# On Windows:
copy .env.example .env
```

Open `.env` and replace `your_anthropic_api_key_here` with your real API key:

```
ANTHROPIC_API_KEY=sk-ant-...
```

Start the Flask server:

```bash
python app.py
```

The backend runs at **http://localhost:5000**

---

### Step 2 — Set up the Frontend

Open a **new terminal** and run:

```bash
cd frontend
npm install
npm start
```

The app opens automatically at **http://localhost:3000**

---

## How It Works

1. User fills in Name, Role, Bio notes, Interests, and an optional Photo URL
2. React frontend sends a **POST** request to `/api/generate-profile`
3. Flask backend calls the **Claude API** with a structured prompt
4. Claude returns a polished JSON profile (name, role, bio, badges, initials)
5. The profile card renders on the frontend with smooth animation

---

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/generate-profile` | Generate a profile card from form data |
| GET | `/api/health` | Health check |

### POST `/api/generate-profile`

**Request body:**
```json
{
  "name": "Alex Johnson",
  "role": "Computer Science Student",
  "bio": "Passionate about web dev and AI",
  "interests": "Python, ML, Open Source",
  "imageUrl": "https://example.com/photo.jpg"
}
```

**Response:**
```json
{
  "name": "Alex Johnson",
  "role": "Computer Science Student",
  "bio": "Alex Johnson is a driven computer science student with a keen focus on web development and artificial intelligence...",
  "badges": ["Python", "Machine Learning", "Open Source", "Web Dev"],
  "initials": "AJ",
  "imageUrl": "https://example.com/photo.jpg"
}
```

---

## Troubleshooting

**Backend won't start?**
- Make sure Python 3.8+ is installed: `python --version`
- Make sure `.env` exists with a valid API key

**Frontend shows "Failed to generate profile"?**
- Confirm the backend is running on port 5000
- Check the terminal where Flask is running for error messages

**npm install fails?**
- Make sure Node.js v16+ is installed: `node --version`
