# Portfolio Website Deployment Using Docker

## Overview

This project demonstrates how to containerize and deploy a simple portfolio website using **Docker and Nginx**.

The website contains:

* Home Page
* About Page
* Contact Page

It runs inside a Docker container using the Nginx web server.

---

## Project Structure

```text id="p9kq7x"
portfolio-website/
│
├── index.html
├── about.html
├── contact.html
├── styles.css
└── Dockerfile
```

---

## Features

* Simple multi-page portfolio website
* Built using HTML and CSS
* Hosted using Nginx inside a Docker container
* Portable and lightweight deployment
* Runs on any system with Docker installed

---

## Dockerfile

```dockerfile id="x1m9tq"
FROM nginx:latest

# Copy website files to Nginx default directory
COPY . /usr/share/nginx/html

# Expose port 80
EXPOSE 80
```

---

## How to Build Docker Image

Run this command inside the project folder:

```bash id="b7kq1a"
docker build -t portfolio-website:v1 .
```

---

## How to Run Docker Container

```bash id="m4p9xz"
docker run -d \
--name portfolio-container \
-p 8081:80 \
portfolio-website:v1
```

---

## Access Website

Open browser:

```text id="z2kq7m"
http://localhost:8081
```

Pages:

* Home → `/index.html`
* About → `/about.html`
* Contact → `/contact.html`

---

## Docker Commands Used

### List Images

```bash id="k9p1wq"
docker images
```

### List Running Containers

```bash id="t7xq2m"
docker ps
```

### Stop Container

```bash id="v3kq8n"
docker stop portfolio-container
```

### Remove Container

```bash id="r6m1pq"
docker rm portfolio-container
```

### Remove Image

```bash id="w8xq3t"
docker rmi portfolio-website:v1
```

---

## Deployment Flow

```text id="d9kq2m"
HTML/CSS Files
      ↓
Dockerfile
      ↓
Docker Build Image
      ↓
Docker Run Container
      ↓
Nginx Server
      ↓
Browser Access (localhost:8080)
```

---

## Technologies Used

* HTML
* CSS
* Docker
* Nginx

---

## Learning Outcomes

After completing this project, you will understand:

* Docker image creation
* Container lifecycle
* Port mapping
* Static website hosting using Nginx
* Basic DevOps containerization workflow

---

## Author

**Madhuri**

Learning DevOps fundamentals:

* Linux
* Git
* Docker
* AWS basics
* CI/CD concepts
