# Monitoring and Observability Platform
 
A monitoring and observability setup built around a Spring Boot bank app (**DevOps-BankApp**). It shows how to watch a running app's health, metrics, and logs using Prometheus, Grafana, Loki, and other tools — all connected with Docker.
 
## 🎯 What This Project Does
 
This repo shows a full monitoring setup for a real app, including:
- **Live metrics** from the app and the server (CPU, memory, requests)
- **Container metrics** (how much resource each Docker container uses)
- **Log collection** from the app, sent to one place for easy searching
- **Dashboards** in Grafana to see everything visually
- **Alerts** when something looks wrong
## 🛠️ Tools Used
 
| Tool | What It Does |
|------|---------------|
| **Spring Boot (Java)** | The bank app itself |
| **MySQL** | Stores the app's data |
| **Docker & Docker Compose** | Runs everything in containers |
| **Prometheus** | Collects and stores metrics |
| **Grafana** | Shows metrics and logs on dashboards |
| **Loki** | Stores logs |
| **Promtail** | Sends logs from the server to Loki |
| **cAdvisor** | Tracks resource usage of each container |
| **node-exporter** | Tracks resource usage of the whole machine |
 
## 📁 Project Structure
 
```
Monitoring-and-Observability/
├── DevOps-BankApp/          # The Spring Boot bank app
│   ├── src/                 # App source code
│   ├── Dockerfile           # Builds the app into a container
│   └── README.md            # App-specific notes
├── docker-compose.yml       # Starts the app + all monitoring tools together
├── prometheus.yml           # Prometheus settings
├── promtail-config.yml      # Promtail settings
└── loki/
    └── loki-config.yml      # Loki settings
```
 
## ✨ Key Features
 
### Metrics
- Real-time app metrics (requests, response time, errors)
- Server-level metrics (CPU, memory, disk)
- Container-level metrics (per Docker container)
### Logs
- App logs collected automatically and sent to Loki
- Searchable through Grafana
### Dashboards
- Visual dashboards in Grafana showing app health and system stats
### Bank App Features
- Sign up and log in (passwords stored safely with BCrypt)
- Deposit, withdraw, and transfer money between accounts
- Transaction history
- Dark/light theme toggle
- Health check at `/actuator/health`
## 🚀 Getting Started
 
### What You Need
- **Docker & Docker Compose** installed
- (Only if running without Docker) **Java 21** and **MySQL 8.0**
### Easiest Way: Run With Docker
 
1. **Clone the repo:**
```bash
   git clone https://github.com/PriyanshuVishwakarma912/Monitoring-and-Observability.git
   cd Monitoring-and-Observability
```
 
2. **Start everything:**
```bash
   docker-compose up -d --build
```
 
3. **Open these in your browser:**
   | Service | Address | Notes |
   |---------|---------|-------|
   | Bank App | http://localhost:8080 | Main app |
   | Grafana | http://localhost:3001 | Dashboards (default login: admin/admin) |
   | Prometheus | http://localhost:9090 | Raw metrics |
   | Loki | http://localhost:3100 | Log storage (used through Grafana) |
   | cAdvisor | http://localhost:8081 | Container stats |
   | MySQL | localhost:3306 | Database |
4. **Stop everything:**
```bash
   docker-compose down
```
 
### Run the App Alone (Without Docker)
 
If you just want to run the bank app without the monitoring tools:
 
```bash
cd DevOps-BankApp
 
# Create the database
mysql -u root -p -e "CREATE DATABASE bankappdb;"
 
# Run the app
./mvnw spring-boot:run
```
 
Then visit http://localhost:8080
 
## 🔧 Configuration
 
Main settings used by Docker Compose:
 
```bash
# Database
MYSQL_ROOT_PASSWORD=Test@123
MYSQL_DATABASE=bankappdb
 
# App connects to database using:
SPRING_DATASOURCE_URL=jdbc:mysql://bankapp-mysql:3306/bankappdb
```
 
You can change these values in `docker-compose.yml` before starting the project.
 
## 🩺 Health Check
 
- App health: `http://localhost:8080/actuator/health`
 
