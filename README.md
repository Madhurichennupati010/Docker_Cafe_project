# ☕ Cafe Website - End-to-End DevOps CI/CD Project using GitHub Actions, Docker, Kubernetes (Minikube) & AWS EC2

# 📌 Project Overview

This project demonstrates a complete **End-to-End DevOps CI/CD Pipeline** for deploying a static Cafe Website using modern DevOps tools.

The website is containerized using Docker, stored in Docker Hub, automatically deployed to a Kubernetes cluster running on **Minikube inside an AWS EC2 instance**, and updated through a **GitHub Actions Self-Hosted Runner** after every code push.

The project also demonstrates Kubernetes features such as:

- Continuous Deployment
- Rolling Updates
- Auto Healing
- Horizontal Pod Autoscaling (HPA)
- Kubernetes Health Checks
- Self-hosted GitHub Actions Runner

---

# 🏗 Architecture

```
Developer
      │
      ▼
GitHub Repository
      │
      ▼
GitHub Actions Workflow
      │
      ▼
Build Docker Image
      │
      ▼
Push Image to Docker Hub
      │
      ▼
AWS EC2 Self-Hosted Runner
      │
      ▼
Minikube Kubernetes Cluster
      │
      ▼
Rolling Deployment
      │
      ▼
Cafe Website
```

---

# 🛠 Technologies Used

| Technology | Purpose |
|------------|----------|
| Git | Version Control |
| GitHub | Source Code Repository |
| GitHub Actions | Continuous Integration & Deployment |
| Docker | Containerization |
| Docker Hub | Image Registry |
| AWS EC2 | Deployment Server |
| Minikube | Local Kubernetes Cluster |
| Kubernetes | Container Orchestration |
| kubectl | Kubernetes CLI |
| Linux | Operating System |

---

# 📂 Project Structure

```
Docker_Cafe_project/

│
├── .github/
│     └── workflows/
│            deploy.yml
│
├── K8s/
│     ├── deployment.yaml
│     ├── service.yaml
│     ├── hpa.yaml
│
├── Dockerfile
├── index.html
├── styles.css
├── README.md
```

---

# 🚀 Features

- Dockerized Cafe Website
- Hosted Docker Image on Docker Hub
- Kubernetes Deployment
- NodePort Service
- GitHub Actions CI/CD
- Self Hosted Runner
- Rolling Updates
- Auto Healing
- Horizontal Pod Autoscaling
- Health Checks
- AWS Deployment

---

# ⚙ CI/CD Pipeline

Whenever code is pushed to the **main** branch:

1. GitHub Actions starts automatically.
2. Repository is cloned.
3. Docker Image is built.
4. Image is pushed to Docker Hub.
5. GitHub Self Hosted Runner receives the job.
6. Kubernetes Deployment image is updated.
7. Rolling update begins.
8. Deployment status is verified.

---

# 🔄 GitHub Actions Workflow

```
Developer Push

      ↓

GitHub Actions

      ↓

Build Docker Image

      ↓

Push Image to Docker Hub

      ↓

Connect to EC2 Self Hosted Runner

      ↓

kubectl set image

      ↓

Rolling Update

      ↓

Deployment Verification
```

---

# 🐳 Docker Image

```
madhu934652/cafe-website
```

---

# ☸ Kubernetes Resources

### Deployment

- Replica Management
- Rolling Updates
- Auto Healing
- Health Checks

---

### Service

```
Type : NodePort
```

Used for exposing the application outside the Kubernetes Cluster.

---

### Horizontal Pod Autoscaler

Configured using

```
autoscaling/v2
```

Features

- Minimum Replicas
- Maximum Replicas
- CPU Utilization based scaling

---

# ❤️ Kubernetes Auto Healing

Auto Healing is implemented using:

- Deployment Controller
- ReplicaSet
- Liveness Probe
- Readiness Probe

### Demonstration

Delete any running pod

```
kubectl delete pod <pod-name>
```

Kubernetes automatically creates a new Pod to maintain the desired replica count.

---

# 📈 Horizontal Pod Autoscaling

Metrics Server is enabled inside Minikube.

HPA automatically increases or decreases the number of Pods based on CPU utilization.

Example

```
kubectl get hpa
```

Generate Load

```
kubectl run load-generator \
--image=busybox \
--restart=Never \
-it -- /bin/sh
```

```
while true
do
wget -q -O- http://cafe-service
done
```

Watch Scaling

```
kubectl get hpa -w
```

```
kubectl get pods -w
```

---

# ❤️ Auto Healing Demonstration

Open Terminal 1

```
kubectl get pods -w
```

Open Terminal 2

```
kubectl delete pod <pod-name>
```

Result

- Old Pod Terminated
- New Pod Created Automatically
- Application Remains Available

---

# 🚀 Deployment Steps

Clone Repository

```
git clone <repository-url>
```

Go to Project

```
cd Docker_Cafe_project
```

Deploy Kubernetes Resources

```
kubectl apply -f K8s/
```

Verify

```
kubectl get all
```

---

# 📊 Verify Deployment

Pods

```
kubectl get pods
```

Deployment

```
kubectl get deployments
```

Service

```
kubectl get svc
```

HPA

```
kubectl get hpa
```

---

# 📷 Screenshots added in the pdf file

- GitHub Repository
- GitHub Actions Success
- Docker Hub Image
- Kubernetes Pods
- Kubernetes Deployment
- Kubernetes Service
- Horizontal Pod Autoscaler
- Auto Healing Demo
- Website Running
- AWS EC2
- Self Hosted Runner

---

# 🎯 Project Highlights

✅ Docker Containerization

✅ GitHub Actions CI/CD

✅ Docker Hub Integration

✅ AWS EC2 Deployment

✅ Kubernetes (Minikube)

✅ Rolling Updates

✅ Auto Healing

✅ Horizontal Pod Autoscaling

✅ Self Hosted GitHub Runner

---

# 👨‍💻 Author

**Chennupati Madhuri**

Cloud & DevOps Engineer

Skills

- AWS
- Docker
- Kubernetes
- GitHub Actions
- Jenkins
- Linux
- Terraform
- CI/CD
- DevOps
