# 🚀 GitHub Actions CI/CD Pipeline with Docker, Flask8, Hadolint, Trivy & DevSecOps

![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-blue?logo=githubactions)
![Docker](https://img.shields.io/badge/Container-Docker-blue?logo=docker)
![Security](https://img.shields.io/badge/Security-DevSecOps-red)
![Trivy](https://img.shields.io/badge/Image%20Scan-Trivy-blue)
![Hadolint](https://img.shields.io/badge/Dockerfile-Hadolint-yellow)
![Bandit](https://img.shields.io/badge/SAST-Bandit-red)
![Gitleaks](https://img.shields.io/badge/Secrets-Gitleaks-orange)
![pip-audit](https://img.shields.io/badge/Dependency-pip--audit-blue)
![Flake8](https://img.shields.io/badge/Lint-Flake8-green)

------------------------------------------------------------------

## 📌 Project Overview

This project demonstrates a **production-grade CI/CD pipeline with integrated DevSecOps practices** using GitHub Actions.

On every code push, the pipeline automatically:

* 🔍 Performs code quality & security checks
* 🐳 Builds a Docker image
* 📦 Pushes it to DockerHub
* 🔐 Connects to a remote server via SSH
* 🚀 Deploys the updated container
* 🧹 Cleans up old containers to prevent port conflicts

---------------------------------------------

## ⚙️ Tech Stack

| Category         | Tools                   |
| ---------------- | ----------------------- |
| CI/CD            | GitHub Actions          |
| Backend          | Flask (Python)          |
| Containerization | Docker                  |
| Web Server       | Gunicorn                |
| Security         | Bandit, Gitleaks, Trivy |
| Code Quality     | Flake8                  |
| Dependency Scan  | pip-audit               |
| Docker Linting   | Hadolint                |
| Deployment       | SSH (AWS / Azure VM)    |

---------------------------------------------

## 🏗️ Architecture

```````````````````
👨‍💻 Developer
     ↓
📦 GitHub Push
     ↓
⚙️ GitHub Actions Pipeline
     ↓
🔍 Code Quality & Security Checks
     ↓
🐳 Docker Build
     ↓
📤 Push to DockerHub
     ↓
🔐 SSH to Remote Server
     ↓
🛑 Stop Old Container
     ↓
🧹 Remove Old Container
     ↓
🚀 Run New Container
     ↓
🌐 Live Application

````````````````````````````````

-------------------------------

## 🔄 CI/CD Workflow

Workflow files are located in:

```
.github/workflows/
```

---

### 🚀 Pipeline Stages

### 1️⃣ Code Checkout

* Fetch latest source code from repository

---

### 2️⃣ Code Quality & Security Checks (CI Phase) 🔍

The pipeline enforces **DevSecOps best practices** before deployment:

* 🧹 **Linting (Code Quality)**

  * Tool: `flake8`
  * Ensures clean and standardized Python code

* 🔐 **SAST (Static Application Security Testing)**

  * Tool: `bandit`
  * Detects security vulnerabilities in code

* 🔑 **Secrets Scanning**

  * Tool: `gitleaks`
  * Prevents exposure of sensitive data

* 📦 **Dependency Vulnerability Scan**

  * Tool: `pip-audit`
  * Checks Python packages for known vulnerabilities

* 🐳 **Dockerfile Linting**

  * Tool: `hadolint`
  * Ensures Docker best practices

* 🛡️ **Container Image Scan**

  * Tool: `trivy`
  * Detects vulnerabilities in Docker images

---

### 3️⃣ Build Phase 🐳

* Build Docker image from application source

---

### 4️⃣ Push to Registry 📦

* Push Docker image to DockerHub

---

### 5️⃣ Deployment (CD Phase) 🚀

* 🔐 SSH into remote server
* 🛑 Stop running container (if exists)
* 🧹 Remove old container
* 🚀 Deploy new container

---

## 🔐 GitHub Secrets

| Secret            | Purpose            |
| ----------------- | ------------------ |
| `HOST`            | Server Public IP   |
| `USERNAME`        | SSH username       |
| `SSH_KEY`         | Private SSH key    |
| `DOCKER_USERNAME` | DockerHub username |
| `DOCKER_PASSWORD` | DockerHub token    |

---

## 🐳 Docker Usage

### Build Image

```
docker build -t <dockerhub-username>/my-image .
```

### Run Container

```
docker run -d -p 80:5000 --name my-app <dockerhub-username>/my-image
```

---

## ⚠️ Common Issues & Fixes

### ❌ Port Already in Use

**Cause:** Old container still running

**Fix:**

```
docker stop $(docker ps -q)
docker rm $(docker ps -aq)
```

---

### ❌ SSH Timeout

**Cause:** Port 22 blocked

**Fix:** Allow SSH in firewall (Security Group / NSG)

---

### ❌ Deployment Failure

**Cause:** Incorrect image name or missing cleanup

**Fix:** Ensure proper Docker image and stop old containers before deployment

---

## 🧠 Key Learnings

* End-to-end CI/CD pipeline implementation
* DevSecOps integration in CI
* Docker container lifecycle management
* Debugging real-world deployment issues
* Secure and automated deployments

---

## 🚀 Future Enhancements

* 🔁 Zero-downtime deployment
* 🌐 Nginx reverse proxy
* 🔒 HTTPS (SSL setup)
* 📊 Monitoring & logging

---

## 📸 Access Application

After deployment:

```
http://<your-server-ip>
```

---

## ⭐ Support

If you found this project useful, consider giving it a ⭐ on GitHub!

---
