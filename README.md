# 🚀 MEAN Stack DevOps Deployment Project

## 📌 Project Overview

This project demonstrates the complete containerization and CI/CD deployment of a full-stack MEAN (MongoDB, Express, Angular, Node.js) application.

The goal of this project is to:

- Containerize frontend and backend applications
- Use Docker Compose for multi-container orchestration
- Configure Jenkins CI/CD pipeline
- Push Docker images to DockerHub
- Deploy the application on an Ubuntu VM
- Configure Nginx reverse proxy (Port 80)

---

# 🏗️ Project Architecture

GitHub (myapp32)  
⬇  
Jenkins (Agent: manik)  
⬇  
Docker Build  
⬇  
DockerHub (malik0505)  
⬇  
Ubuntu VM (Docker Compose)  
⬇  
MongoDB + Backend + Frontend  
⬇  
Nginx Reverse Proxy (Port 80)  
⬇  
Live Application  


---



---

# 🐳 Docker Configuration

## 1️⃣ Backend Dockerfile

- Uses Node.js 18 Alpine
- Installs dependencies
- Exposes port 5000
- Runs server.js

## 2️⃣ Frontend Dockerfile

- Multi-stage build
- Builds Angular production build
- Uses Nginx to serve static files
- Exposes port 80

---

# 🗄️ Docker Compose Configuration

Services included:

- MongoDB (Official Image)
- Backend
- Frontend
- Nginx Reverse Proxy

To run manually:

```bash
docker-compose up -d



☁️ Ubuntu VM Setup (AWS / Azure)
Install Docker
sudo apt update
sudo apt install docker.io docker-compose nginx -y
sudo usermod -aG docker ubuntu
Clone Repository
git clone https://github.com/myapp32/mean-crud-devops.git
cd mean-crud-devops
Run Application
docker-compose up -d



