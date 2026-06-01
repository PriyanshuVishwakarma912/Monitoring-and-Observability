# DevOps-BankApp

A Spring Boot banking application used as a base for learning end-to-end DevOps — Docker.

## Tech Stack

- **Backend:** Spring Boot 3.4.1, Java 21, Spring Security, JPA/Hibernate
- **Frontend:** Thymeleaf, Bootstrap 5, Glassmorphism UI with dark/light theme
- **Database:** MySQL 8.0
- **DevOps:** Docker, GitHub Actions
## Branch

| Branch | Description |
|--------|-------------|
| `start` | Modernized app — full backend + frontend (developer handoff) |Adds Dockerfile, multi-stage build, docker-compose |


See [ROADMAP.md](ROADMAP.md) for the full progression.

## Quick Start

### Run locally (needs Java 21 + MySQL)

```bash
# Create database
mysql -u root -p -e "CREATE DATABASE bankappdb;"

# Run the app
./mvnw spring-boot:run
```

### Run with Docker (recommended)

# Start everything
docker compose up -d --build

# Visit http://localhost:8080
```

# Start everything
docker compose up -d --build



## Features

- User registration & login with BCrypt passwords
- Deposit, withdraw, transfer between accounts
- Transaction history with color-coded entries
- Dark/light theme toggle (persists across sessions)
- Health check at `/actuator/health`
