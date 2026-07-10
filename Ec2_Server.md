# 🚀 AWS EC2 Server Setup

## Step 1: Launch an EC2 Instance

- OS: Ubuntu 24.04 LTS
- Instance Type: t3.medium (Recommended)
- Storage: 30 GB
- Security Group:
  - SSH (22)
  - HTTP (80)
  - HTTPS (443)
  - Custom TCP (30080) (NodePort)
  - Custom TCP (8080) (Optional)

---

## Step 2: Connect to EC2

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>
```
# Update Packages

```bash
sudo apt update
sudo apt upgrade -y
```

---

# Install Git

```bash
sudo apt install git -y
```

Verify

```bash
git --version
```

---

# Install Docker

```bash
sudo apt install docker.io -y

sudo systemctl enable docker

sudo systemctl start docker

sudo usermod -aG docker $USER
```

Reconnect to the server

```bash
exit
```

SSH again

Verify

```bash
docker --version
```

---

# Install kubectl

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s \
https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

chmod +x kubectl

sudo mv kubectl /usr/local/bin/
```

Verify

```bash
kubectl version --client
```

---

# Install Minikube

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verify

```bash
minikube version
```

---

# Start Minikube

```bash
minikube start --driver=docker
```

Verify

```bash
minikube status
```

---

# Clone GitHub Repository

```bash
git clone https://github.com/Madhurichennupati010/Docker_Cafe_project.git

cd Docker_Cafe_project
```

# Deploy Kubernetes Resources

```bash
kubectl apply -f K8s/
```

---

# Verify Deployment

Pods

```bash
kubectl get pods
```

Deployments

```bash
kubectl get deployments
```

Services

```bash
kubectl get svc
```

---

# Enable Metrics Server

```bash
minikube addons enable metrics-server
```

Verify

```bash
kubectl top nodes
```

---

# Verify HPA

```bash
kubectl get hpa
```

---

# Watch Pods

```bash
kubectl get pods -w
```

---

# Test Auto Healing

Check Pods

```bash
kubectl get pods
```

Delete a Pod

```bash
kubectl delete pod <pod-name>
```

Watch New Pod Creation

```bash
kubectl get pods -w
```

---

# Test Auto Scaling

Create Load Generator

```bash
kubectl run load-generator \
--image=busybox \
--restart=Never \
-it -- /bin/sh
```

Inside BusyBox

```sh
while true
do
wget -q -O- http://cafe-service
done
```

Watch HPA

```bash
kubectl get hpa -w
```

Watch Pods

```bash
kubectl get pods -w
```

---

# Verify Deployment Rollout

```bash
kubectl rollout status deployment/cafe-app
```

Deployment History

```bash
kubectl rollout history deployment/cafe-app
```

Restart Deployment

```bash
kubectl rollout restart deployment/cafe-app
```

---

# Verify Running Containers

```bash
docker ps
```

Docker Images

```bash
docker images
```

---

# Access the Application

Check Service

```bash
kubectl get svc
```

Open in Browser

```text
http://<EC2_PUBLIC_IP>:30080
```

---

# Useful Kubernetes Commands

```bash
kubectl get all
```

```bash
kubectl describe pod <pod-name>
```

```bash
kubectl logs <pod-name>
```

```bash
kubectl describe deployment cafe-app
```

```bash
kubectl describe svc cafe-service
```

```bash
kubectl get events
```

```bash
kubectl get nodes
```

```bash
kubectl get namespaces
```

---

# Stop Minikube

```bash
minikube stop
```

---

# Start Minikube Again

```bash
minikube start
```

---

# Delete Minikube Cluster

```bash
minikube delete
```
