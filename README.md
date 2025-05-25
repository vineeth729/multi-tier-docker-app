# 🚀 Multi-Tier Dockerized Application Deployment

![Docker Compose](https://img.shields.io/badge/docker--compose-enabled-blue?logo=docker)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-13+-blue?logo=postgresql)
![Flask](https://img.shields.io/badge/Flask-Python%203.9+-yellow?logo=flask)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Build](https://img.shields.io/badge/Build-Passing-brightgreen)

This project showcases a **multi-tier application** deployed using **Docker Compose** on a **cloud-based virtual machine**. The architecture includes a frontend served via Nginx, an API built with Flask, and a PostgreSQL backend for persistent data storage.

---

## 📚 Table of Contents

- [🧩 Architecture](#-architecture)
- [⚙️ Setup & Deployment](#️-setup--deployment)
- [🔓 Exposed Ports](#-exposed-ports)
- [🖼️ Screenshots](#️-screenshots)
- [🗂️ Folder Structure](#️-folder-structure)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)

## 🧩 Architecture
---
Frontend (HTML + Nginx)  <--->  API (Python Flask)  <--->  PostgreSQL (Database)
         :8080                        :5000                       :5432 (internal)

- **Frontend**: Serves a simple HTML UI via Nginx.
- **API**: Handles HTTP requests, connects to PostgreSQL.
- **Database**: Stores and serves persistent data to the API.

---

## ⚙️ Setup & Deployment

### 🖥️ Prerequisites

- Cloud VM (e.g., AWS EC2 Ubuntu)
- Open ports: `22`, `8080`, `5000`
- Installed:
  - `Docker`
  - `Docker Compose`
  - `Git`

### 🔧 Deployment Steps

```bash
# SSH into your cloud VM
ssh -i your-key.pem ubuntu@<your-vm-ip>

# Install Docker, Docker Compose, and Git if needed
sudo apt update
sudo apt install -y docker.io git
sudo systemctl start docker && sudo systemctl enable docker

# Install Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
  -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose

# Clone the repository
git clone https://github.com/<your-username>/multi-tier-docker-app.git
cd multi-tier-docker-app

# Deploy the app
sudo docker-compose up --build -d
```
| Component | Port | Description              |
| --------- | ---- | ------------------------ |
| Frontend  | 8080 | Public access via Nginx  |
| API       | 5000 | Flask REST API           |
| Database  | 5432 | Internal PostgreSQL port |

multi-tier-docker-app/
├── api/
│   ├── app.py
│   ├── Dockerfile
│   └── requirements.txt
├── frontend/
│   ├── Dockerfile
│   └── index.html
├── docker-compose.yml
└── README.md



