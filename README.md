# 🚀 Modern DevOps Portfolio Deployment

## 📌 Project Overview
This project demonstrates an end-to-end CI/CD pipeline for deploying a containerized portfolio application to AWS EC2 using Docker and GitHub Actions.

The application is automatically built, pushed, and deployed whenever code is pushed to the repository.

---

## 🧠 Architecture

GitHub → GitHub Actions → Docker Hub → AWS EC2 → Nginx (Reverse Proxy) → Browser

---

## ⚙️ Tech Stack

- CI/CD: GitHub Actions  
- Containerization: Docker  
- Cloud: AWS EC2  
- Web Server: Nginx (Reverse Proxy)  
- Registry: Docker Hub  

---

## 🔄 CI/CD Workflow

1. Code is pushed to GitHub  
2. GitHub Actions triggers pipeline  
3. Docker image is built  
4. Image is pushed to Docker Hub  
5. Pipeline connects to EC2 via SSH  
6. Existing container is stopped and removed  
7. New container is deployed automatically  

---

## 🐳 Docker Setup

### Build Image
```bash
docker build -t sidh25/portfolio .
```

### Run Container
```bash
docker run -d -p 3000:80 --name portfolio sidh25/portfolio
```

---

## 🌐 Nginx Reverse Proxy

Nginx is configured on EC2 to forward traffic from port 80 to the container running on port 3000.

```nginx
location / {
    proxy_pass http://localhost:3000;
}
```

---

## 🚀 Deployment

The application is deployed on an AWS EC2 instance and exposed via a public IP.

Access the application:
```
http://3.110.222.205
```

---

## ⚠️ Challenges Faced

- EC2 Public IP changed after instance restart causing CI/CD failure  
- Fixed by updating GitHub Secrets (EC2_HOST)  
- Implemented reverse proxy using Nginx to follow industry standards  

---

## 📸 Screenshots

- CI/CD Pipeline Success  
- Docker Container Running  
- EC2 Instance Running  
- Nginx Configuration  
- Live Application  

---

## 🎯 Key Learnings

- End-to-end CI/CD pipeline implementation  
- Docker image creation and deployment  
- AWS EC2 networking and security groups  
- Reverse proxy using Nginx  
- Debugging real-world deployment issues  

---

## 👨‍💻 Author

Siddhesh Pallor
