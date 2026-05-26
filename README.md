# Dockerized 3-Tier Web Application (Nginx + Flask + MySQL)

This project demonstrates a **containerized 3-tier web application architecture** using Docker Compose.

It includes:

- **Nginx** as a reverse proxy (frontend entry point)
- **Flask** as backend API service
- **MySQL** as the database (secured and internal only)

All services communicate through a Docker bridge network, ensuring secure and isolated communication between layers.

---

## Architecture

```
        [ User Browser ]
                |
                v
 [ Nginx Reverse Proxy : Port 80 ]
                |
                v
   [ Flask Application (Backend API) ]
                |
                v
 [ MySQL Database (Private Container - No Public Exposure) ]
```

---

## Features

- Dockerized multi-container setup
- Nginx reverse proxy for routing requests
- Flask REST API backend
- MySQL database integration
- Persistent database storage using Docker volumes
- Secure database (not exposed to host machine)
- Fully containerized deployment using Docker Compose

---

## Prerequisites

Make sure you have the following installed:

- Docker
- Docker Compose
- Git (optional)

---

## Clone Repository

```bash
git clone <repo-url>
cd <project-folder>
```

---

## Configuration

Create a `.env` file (recommended):

```env
MYSQL_HOST=mysql
MYSQL_USER=your_username
MYSQL_PASSWORD=your_password
MYSQL_DB=your_database
```

---

## Run the Application

```bash
docker compose up --build -d
```

---

## Access the Application

### Frontend (via Nginx)

http://localhost

### Flask Backend (internal only)

http://localhost:5000

> Backend is not exposed publicly in production setups.

---

## Database Access (Inside Container)

```bash
docker exec -it mysql mysql -u root -p
```

Inside MySQL:

```sql
USE devops;
SHOW TABLES;
SELECT * FROM messages;
```

---

## Stop Containers

```bash
docker compose down
```

---

## Security Design

- MySQL is NOT exposed to the host machine
- Only Flask communicates with MySQL internally
- Nginx is the single public entry point
- Docker network ensures secure service-to-service communication

---

## Key Learning Outcomes

- Docker multi-container orchestration
- Reverse proxy setup using Nginx
- Flask + MySQL integration
- Docker networking concepts
- Persistent storage using volumes
- Basic 3-tier architecture implementation

---

## ⚠️ Notes

This project is for learning and demonstration purposes.

In production:

- Use `.env` files or secrets manager
- Enable HTTPS in Nginx
- Secure database credentials
- Add health checks and logging improvements
