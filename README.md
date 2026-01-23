# Docker Lab: Creating a Dockerfile for Flask Application

## Overview

In this lab, you'll learn how to create a Dockerfile that packages a simple web application into a container image, and then run it locally.

## Prerequisites

- Docker Desktop or Docker Engine installed
- Basic knowledge of Linux commands

## Quick Start

### Build the Docker image:
```bash
docker build -t flask-app .
```

### Run the container:
```bash
docker run -d -p 5000:5000 flask-app
```

### Test the application:
Open your browser and navigate to: `http://localhost:5000`

Or use curl:
```bash
curl http://localhost:5000
```

## Project Structure

```
docker-lab/
├── app.py              # Flask application
├── Dockerfile          # Docker image configuration
├── .dockerignore       # Files to exclude from image
├── requirements.txt    # Python dependencies
└── README.md          # This file
```

## Managing Your Container

### View running containers:
```bash
docker ps
```

### View logs:
```bash
docker logs <container-id>
```

### Stop the container:
```bash
docker stop <container-id>
```

### Remove the container:
```bash
docker rm <container-id>
```

### Remove the image:
```bash
docker rmi flask-app
```

## Next Steps

- Add more routes to your Flask application
- Implement a multi-stage build
- Use Docker Compose
- Push your image to Docker Hub

## Resources

- [Docker Official Documentation](https://docs.docker.com/)
- [Flask Documentation](https://flask.palletsprojects.com/)
