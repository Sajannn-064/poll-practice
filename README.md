# Live Poll
 
A small web app where people create a poll, share a link, vote, and watch the results update live on every screen.
 
Built as a 14-day, 1-hour-a-day practice sprint, by two people working in one repo.
 
## Progress
 
Tick these off as you build them (change `[ ]` to `[x]`).
 
**Core**
- [ ] Create a poll
- [ ] View a poll
- [ ] Vote on a poll
- [ ] Live results with WebSockets
- [ ] Tailwind styling
- [ ] Deployed online
**Extras**
- [ ] AI-suggested poll options (Gemini)
- [ ] Poll statistics (totals, percentages, leader)
- [ ] CSV export of results
- [ ] Share box with copy-link and QR code
- [ ] Poll templates
## Tech stack
 
| Part | Tool |
|---|---|
| Frontend | React + Vite, Tailwind CSS |
| Backend | Python, FastAPI, Uvicorn |
| Database | SQLite (a simple file-based database) |
| Live updates | WebSockets |
| AI | Google Gemini API |
| Hosting | Vercel (frontend), Render (backend) |
 
## Project structure
 
```
poll-practice/
├── backend/
│   ├── main.py            # app entry point and routes
│   ├── stats.py           # statistics functions
│   ├── export.py          # CSV export
│   ├── templates.py       # ready-made poll templates
│   └── requirements.txt   # Python libraries needed
├── frontend/
│   └── src/
│       └── components/    # React components
├── .gitignore
└── README.md
```
 
Adjust this to match the real folders once they exist.
 
## Run it locally
 
You need Python 3 and Node.js installed.
 
### 1. Backend
 
```
cd backend
python3 -m venv venv
source venv/bin/activate      # on Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload
```
 
The backend runs at http://127.0.0.1:8000. FastAPI also gives you a test page at http://127.0.0.1:8000/docs where you can try every endpoint by clicking.
 
### 2. Frontend
 
Open a second terminal:
 
```
cd frontend
npm install
npm run dev
```
 
The app opens at the address Vite prints (usually http://localhost:5173).
 
## Settings (environment variables)
 
Never commit real keys. Copy `.env.example` to `.env` and fill in the values.
 
| Name | Where | What it is |
|---|---|---|
| `GEMINI_API_KEY` | backend |  Google Gemini API key |
| `VITE_API_URL` | frontend | Address of the backend, e.g. `http://127.0.0.1:8000` |
 
## API endpoints
 
A poll looks like this:
 
```
{
  "id": 1,
  "question": "Best momo place?",
  "options": [
    { "id": 1, "text": "Place A", "votes": 7 },
    { "id": 2, "text": "Place B", "votes": 3 }
  ]
}
```
 
| Method | Path | What it does |
|---|---|---|
| GET | `/polls` | List all polls |
| POST | `/polls` | Create a poll |
| GET | `/polls/{id}` | Get one poll |
| POST | `/polls/{id}/vote` | Add one vote to an option |
| GET | `/polls/{id}/stats` | Totals, percentages and leader |
| GET | `/polls/{id}/export` | Results as CSV |
| GET | `/templates` | Ready-made poll ideas |
| POST | `/ai/suggest-options` | AI suggests options for a topic |
| WebSocket | `/ws/polls/{id}` | Live updates when someone votes |
 
## How we work (git)
 
- Nobody pushes directly to `main`.
- Every change goes on a branch (`feat/...`), then a pull request, then the other person reviews it before it is merged.
- Start every session with `git pull` on `main`.
- Never force-push.
## Team
 
- **Person 1:** core backend, main React pages, live updates, deployment
- **Person 2:** stats, CSV export, stats panel, share box, poll templates
## Live demo
 
link-- 