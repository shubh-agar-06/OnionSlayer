# Onion Slayer

## Dark Web Threat Actor De-anonymization Platform

**Smart India Hackathon problem statement:** Dark web threat actor de-anonymization  
**Organization:** National Technical Research Organisation (NTRO)

Onion Slayer is a cyber threat intelligence platform that helps analysts correlate dark-web marketplace identities and investigate relationships between vendors, aliases, PGP keys, wallets and infrastructure indicators.

The platform provides:

- Vendor and identity resolution across marketplace data
- Interactive relationship graph visualization
- Search across vendors and identifiers
- Infrastructure indicator analysis
- Timeline and confidence analysis
- Analyst review of identity suggestions
- CSV, JSON and report exports

## Technology stack

- **Frontend:** React, Vite, Cytoscape.js and React Force Graph
- **Backend:** Python, Flask and NetworkX
- **Database:** MySQL 8.x
- **Analysis:** SQLAlchemy, scikit-learn, Sentence Transformers and PyTorch

## Quick start — Windows

### Prerequisites

Install and start:

- Python 3.11+
- Node.js LTS
- MySQL 8.x

### 1. Clone the project

```powershell
git clone <repository-url>
cd OnionSlayer
```

### 2. Run setup

Replace the password with your MySQL `root` password:

```powershell
$env:DB_PASSWORD="your_mysql_password"
.\setup.ps1 -SkipDataImport -GenerateSynthetic
```

This creates the Python environment, initializes the database schema, generates demo data and installs frontend dependencies.

If PowerShell blocks the script:

```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

### 3. Start the backend

Open PowerShell terminal 1:

```powershell
$env:DB_HOST="localhost"
$env:DB_USER="root"
$env:DB_PASSWORD="your_mysql_password"
$env:DB_NAME="main_db"

cd backend
..\.venv\Scripts\python.exe app.py
```

Backend: [http://localhost:5000](http://localhost:5000)

### 4. Start the frontend

Open PowerShell terminal 2:

```powershell
cd frontend
npm run dev
```

Open the URL shown by Vite, normally [http://localhost:5173](http://localhost:5173).

## Configuration

| Variable | Default |
|---|---|
| `DB_HOST` | `localhost` |
| `DB_PORT` | `3306` |
| `DB_USER` | `root` |
| `DB_PASSWORD` | `root` |
| `DB_NAME` | `main_db` |

## Verify

```powershell
Invoke-RestMethod http://localhost:5000/
```

## Development commands

Backend tests:

```powershell
cd backend
..\.venv\Scripts\python.exe -m unittest discover -s tests
```

Frontend build:

```powershell
cd frontend
npm run build
```

## Project structure

```text
OnionSlayer/
├── backend/       Flask API, analysis services, graph logic and tests
├── data/          Sample marketplace and infrastructure datasets
├── docs/           Presentation, architecture and demo documentation
├── frontend/      React analyst dashboard
├── setup.ps1      Windows setup script
└── requirements.txt
```

For more details, see [backend/README.md](backend/README.md), [frontend/README.md](frontend/README.md), and the [documentation folder](docs/).
