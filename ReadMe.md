# 🚀 Gitea + Jenkins CI/CD with Nginx  

Modern software teams need flexible and automated pipelines to keep code delivery fast and reliable. While **Gitea** provides lightweight, self-hosted Git repository management, many organizations prefer to leverage the mature **Jenkins** ecosystem for automation.  

By integrating Gitea with Jenkins, we get the best of both worlds:  
- ✅ A simple, private Git service  
- ✅ A powerful and extensible CI/CD engine  

This project demonstrates how to integrate Gitea and Jenkins for CI/CD. We’ll explore both webhook-based triggers and Jenkins’ Gitea plugin, then walk through creating a pipeline that runs automatically on code pushes and pull requests.  

Since we always like **dockerized environments**, everything is deployed using **Docker** and **Docker Compose**. The goal: edits to `index.html` are auto-deployed to an **Nginx container**.  

---

## 📦 Prerequisites  

- One Linux host with **Docker & Docker Compose (v2)**  
- Free ports:  
  - Gitea: `3000` (HTTP), `2222` (SSH)  
  - Jenkins: `8081`  
  - Nginx: `8080`  
- Firewall rules opened (e.g., via `firewalld`)  
- SELinux configured not to block Docker services  

⚠️ Note: This setup is for **demo purposes**. Production environments require hardened security, scaling, and monitoring.  

---

## 🛠️ Setup  

### 1. Clone repository  

```bash
git clone <your-repo-url>
cd basic-gitea-jenkins-ci-cd
docker compose up -d
```
### 2. Initialize Webserver

```
docker run --rm -v webroot:/w bash -lc 'echo "initial - it works!" > /w/index.html'

```

### 3. Access services

```
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword


```