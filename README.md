# RefillMap — Full-Stack Campus Water Refill Finder

A full-stack starter project built with **React + Vite**, **Java 21 + Spring Boot**, and **PostgreSQL**.

## Features
- Browse campus water refill stations.
- Search by station, building, or landmark.
- Filter by cold water, normal water, and working stations.
- Select a starting building and estimate walking time.
- View station details and operational status.
- Submit issue reports that persist in PostgreSQL.
- Issue reports can update station status for demo purposes:
  - `LOW_PRESSURE` -> station becomes Low Pressure
  - `NOT_WORKING` -> station becomes Under Maintenance
  - `WATER_NOT_COLD` -> temperature becomes Normal
  - `FILTER_MAINTENANCE` -> report is saved without automatically changing status
- Seeded sample data for local demos.

> **Demo data note:** The locations and walking times are illustrative sample data, not verified campus information. Reports are stored in the database but are not independently verified by staff.

## Architecture
- `frontend/`: React + Vite UI
- `backend/`: Spring Boot REST API + Spring Data JPA
- `docker-compose.yml`: PostgreSQL database

## Run locally

### Requirements
- Java 21+
- Node.js 20+
- Docker Desktop (recommended) or PostgreSQL 15+

### 1. Start PostgreSQL
From the project root:
```bash
docker compose up -d db
```
PostgreSQL runs on `localhost:5432` with:
- Database: `refillmap`
- Username: `refillmap`
- Password: `refillmap_dev_password`

### 2. Start the backend
```bash
cd backend
./mvnw spring-boot:run
```
On Windows PowerShell:
```powershell
.\mvnw.cmd spring-boot:run
```
The API runs at `http://localhost:8080`.

If Maven Wrapper files are not included in your environment, use an installed Maven:
```bash
mvn spring-boot:run
```

### 3. Start the frontend
Open a second terminal:
```bash
cd frontend
npm install
npm run dev
```
Open the Vite URL printed in the terminal (normally `http://localhost:5173`).

### Alternative: run the entire stack with Docker
```bash
docker compose up --build
```
This starts PostgreSQL, backend, and frontend containers.

## API overview

| Method | Endpoint | Purpose |
|---|---|---|
| `GET` | `/api/stations` | List stations; optional `building`, `search`, `filter` query params |
| `GET` | `/api/stations/{id}` | Get one station |
| `POST` | `/api/stations/{id}/reports` | Create an issue report |
| `GET` | `/api/reports` | List recent reports (demo/admin view) |
| `GET` | `/api/health` | Health check |

### Example issue report
```json
{
  "issueType": "LOW_PRESSURE",
  "comment": "Water is coming out slowly"
}
```

## Before production
- Add authentication and role-based access for students and maintenance staff.
- Require staff review before a report changes the public station status.
- Add rate limiting, spam protection, audit logs, and input moderation.
- Replace sample buildings and walking-time estimates with verified campus data.
- Add tests, database migrations (Flyway), monitoring, backups, and deployment secrets.
