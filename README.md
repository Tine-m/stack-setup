# How to run Spring Boot MVC App with JPA and Postgres DB

App runs locally in IntelliJ, uses Compose only for Postgres (+ pgAdmin)

- ```docker-compose.yml``` for Postgres + pgAdmin
- ```application.properties``` configure the app to use the DB in Docker

From the project root run:

```bash
docker compose up -d
```

Start the Spring Boot app from ```IntelliJ``` (Run/Debug).

- API on ```http://localhost:8080```
- Postgres on ```localhost:5432```
- pgAdmin on ```http://localhost:5050```
  (login with the pgAdmin creds from ```docker-compose.yml```; add a server ```Host=host.docker.internal``` or ```localhost```, ```User=app```, ```Password=app```)
