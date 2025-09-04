# How to run Spring Boot MVC App with JPA and Postgres DB
This repository is prepared for **Java + JPA + PostgreSQL** development.

App runs locally in IntelliJ, uses Compose only for Postgres (+ pgAdmin)

- ```docker-compose.yml``` for Postgres + pgAdmin
- ```application.properties``` configure the app to use the DB in Docker

From the project root run:

```bash
docker compose up -d
docker ps
```

Start the Spring Boot app from ```IntelliJ``` (Run/Debug).

- API on ```http://localhost:8080```
- Postgres on ```localhost:5432```
- pgAdmin on ```http://localhost:5050```
  (login with the pgAdmin creds from ```docker-compose.yml```; add a server ```Host=host.docker.internal``` or ```localhost```, ```User=app```, ```Password=app```)

## ✅ Verify Postgres is up

### With pgAdmin (browser)

1. Open [http://localhost:5050](http://localhost:5050)
2. Login with:
    - **Email:** `admin@example.com`
    - **Password:** `admin`
3. Add a new Server in pgAdmin:
    - **Name:** `local-db`
    - **Connection → Host:** `host.docker.internal` (or `localhost`)
    - **Port:** `5432`
    - **Username:** `app`
    - **Password:** `app`
4. Expand **local-db → Databases** and confirm that `appdb` exists.


---

## 🌐 Smoke test the API

Assuming you have a `StudentController` with a `/students` endpoint:

### A) In browser / curl

- Run in terminal:
```bash
curl http://localhost:8080/students
```

Expected output (first run):
```json
[]
```
(empty list, since no students are saved yet)

Insert student:
```curl
curl -X POST http://localhost:8080/students -H "Content-Type: application/json" -d '{"name":"Alice"}'
```
If you’re on PowerShell (Windows), you may need to escape quotes differently:
```curl
curl -X POST http://localhost:8080/students -H "Content-Type: application/json" -d "{""name"":""Alice""}"

```
