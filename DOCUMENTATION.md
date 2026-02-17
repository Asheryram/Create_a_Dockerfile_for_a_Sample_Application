# Project Documentation: Dockerizing a Flask Application



This project demonstrates how to **containerize a Python Flask web application using Docker**. You are packaging a simple web application into a portable Docker container that can run consistently across any environment.

---

## Project Components

### 1. Flask Application (`app.py`)

A minimal Python web server using the Flask framework:
- Creates a single route at the root URL (`/`)
- Returns the message "Hello from Docker!" when accessed
- Runs on port 5000 and listens on all network interfaces (`0.0.0.0`)

### 2. Python Dependencies (`requirements.txt`)

The application requires two packages:
| Package | Version | Purpose |
|---------|---------|---------|
| Flask | 2.3.0 | Web framework for handling HTTP requests |
| Gunicorn | 21.2.0 | Production-grade WSGI HTTP server |

### 3. Dockerfile

The Dockerfile defines how to build the container image:

| Instruction | What It Does |
|-------------|--------------|
| `FROM python:3.9-slim` | Uses a lightweight Python 3.9 base image |
| `WORKDIR /app` | Sets the working directory inside the container |
| `COPY requirements.txt .` | Copies dependency file first (for layer caching) |
| `RUN pip install...` | Installs Python dependencies |
| `COPY . .` | Copies the application code |
| `EXPOSE 5000` | Documents that the app uses port 5000 |
| `CMD [...]` | Runs Gunicorn to serve the Flask app |

---

## The Workflow

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Source Code   │ ──▶ │  Docker Build   │ ──▶ │  Docker Image   │
│   (app.py)      │     │                 │     │  (flask-app)    │
└─────────────────┘     └─────────────────┘     └─────────────────┘
                                                        │
                                                        ▼
                                                ┌─────────────────┐
                                                │   Container     │
                                                │  (Running App)  │
                                                └─────────────────┘
```

1. **Write** your Flask application code
2. **Define** dependencies in `requirements.txt`
3. **Create** a Dockerfile with build instructions
4. **Build** the Docker image using `docker build`
5. **Run** the container using `docker run`
6. **Access** your app at `http://localhost:5000`

---

## Key Learning Objectives

- **Containerization**: Packaging an application with all its dependencies
- **Dockerfile Syntax**: Understanding Docker instructions (FROM, COPY, RUN, CMD, etc.)
- **Layer Caching**: Optimizing builds by copying `requirements.txt` before app code
- **Port Mapping**: Exposing container ports to the host machine
- **Production Deployment**: Using Gunicorn instead of Flask's development server

---

## Commands Reference

| Command | Purpose |
|---------|---------|
| `docker build -t flask-app .` | Build the image |
| `docker run -d -p 5000:5000 flask-app` | Run the container |
| `docker ps` | List running containers |
| `docker logs <id>` | View container logs |
| `docker stop <id>` | Stop the container |

---

## Why This Matters

By containerizing your application, you achieve:
- **Consistency**: Same environment in development, testing, and production
- **Portability**: Run anywhere Docker is installed
- **Isolation**: Dependencies don't conflict with the host system
- **Scalability**: Easy to deploy multiple instances
