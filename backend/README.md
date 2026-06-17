# Derive AI Notebook Backend

Express + TypeScript API for notes persistence, Auth0-protected requests, AI chat, and OpenRouter-powered math actions.

## Setup

1. Install dependencies:

```bash
cd backend
npm install
```

2. Configure environment variables:

```bash
cp .env.example .env
```

Set `.env`:

```env
PORT=3001
MONGODB_URI=your-mongodb-atlas-connection-string
NODE_ENV=development

AUTH0_DOMAIN=your-auth0-domain
AUTH0_AUDIENCE=your-auth0-audience

GEMINI_API_KEY=your-gemini-api-key
GEMINI_MODEL=gemini-flash-latest

OPENROUTER_API_KEY=your-openrouter-api-key
OPENROUTER_SOLVER_MODEL=openai/gpt-4
OPENROUTER_RECOGNITION_MODEL=openai/gpt-5.2-chat
OPENROUTER_CHECK_MODEL=openai/gpt-5.2-chat
YOUR_SITE_URL=http://localhost:3001
```

3. Start the backend:

```bash
npm run dev
```

Server URL: `http://localhost:3001`

## AI Models

This backend uses OpenRouter for math and vision requests, plus Gemini for chat:

- **Equation solving** (`/api/solve`): uses `OPENROUTER_SOLVER_MODEL`.
- **Handwriting recognition** (`/api/recognize`, `/api/graph`, `/api/nextstep`): uses `OPENROUTER_RECOGNITION_MODEL`.
- **Work checking** (`/api/check`): uses `OPENROUTER_CHECK_MODEL`.
- **Chat** (`/api/chat`): uses Gemini API (`GEMINI_MODEL`) for interactive conversations.

## Endpoints

- `GET /health` - Health check
- `GET /api/notes` - Get all notes
- `GET /api/notes/:id` - Get a specific note
- `POST /api/notes` - Create a new note
- `PUT /api/notes/:id` - Update a note
- `DELETE /api/notes/:id` - Delete a note
- `POST /api/notes/bulk` - Bulk save notes
- `POST /api/chat` - AI chat
- `POST /api/solve` - Recognize and solve handwritten math or solve provided LaTeX
- `POST /api/graph` - Recognize handwritten math for graphing
- `POST /api/recognize` - Recognize handwritten math
- `POST /api/nextstep` - Generate a next step for a math problem
- `POST /api/check` - Check shown mathematical work
