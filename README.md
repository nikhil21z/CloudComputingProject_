# 🚀 Dockerized Visitor Counter with Kubernetes

A Flask-based Visitor Counter application built using **Docker, Redis, and Kubernetes**, featuring horizontal pod autoscaling, health monitoring, self-healing, and hybrid deployment configurations.

## 📌 Project Overview

This project demonstrates how a Python Flask application can be containerized, integrated with Redis, and deployed using Kubernetes.

It explores container orchestration, workload scaling, application health checks, resource management, and hybrid deployment configurations.

## 🐳 Docker Dashboard

![Docker Dashboard Running](./Screenshots/Docker_Dashboard_Running.png)

## 🛠️ Tech Stack

- **Backend:** Python, Flask
- **Database / Cache:** Redis
- **Containerization:** Docker, Docker Compose
- **Orchestration:** Kubernetes, Kind
- **Autoscaling:** Kubernetes Horizontal Pod Autoscaler (HPA)
- **Web Server:** Gunicorn, Nginx
- **Tools:** PowerShell, kubectl

## ✨ Key Features

- Flask-based visitor counter.
- Redis integration for storing visitor counts.
- Optimized multi-stage Docker image.
- Docker Compose for local deployment.
- Kubernetes Deployments and Services.
- Horizontal Pod Autoscaling based on CPU utilization.
- Minimum 2 and maximum 6 web replicas.
- Liveness and readiness probes.
- CPU and memory resource requests and limits.
- Kubernetes self-healing through automatic pod replacement.
- CPU-intensive endpoint for autoscaling demonstrations.
- Hybrid deployment and Nginx failover configuration.

## 🏗️ Architecture

![Project Architecture](docs/architecture.png)

The application uses Flask as its web layer and Redis for visitor-count storage. Docker packages the application, while Kubernetes manages deployment, service discovery, health monitoring, and scaling.

## 📂 Project Structure

```text
CloudComputingProject_/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   ├── static/
│   └── templates/
│
├── docs/
│   ├── architecture.png
│   └── screenshots/
│
├── k8s/
│   ├── before/
│   ├── hpa.yaml
│   ├── redis-deployment.yaml
│   ├── redis-service.yaml
│   ├── web-deployment.yaml
│   └── web-service.yaml
│
├── kind/
├── hybrid/
├── scripts/
├── tools/
│
├── Dockerfile
├── docker-compose.yml
├── README.md
└── .dockerignore
```

## ⚙️ Getting Started

### Prerequisites

- Docker Desktop
- Kubernetes / kubectl
- Kind
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/nikhil21z/CloudComputingProject_.git

cd CloudComputingProject_
```

### 2. Run Using Docker Compose

```bash
docker compose up --build
```

Open in your browser:

```text
http://localhost:5000
```

### 3. Deploy Using Kubernetes

Create a Kind cluster:

```bash
kind create cluster --name private --config kind/private.yaml
```

Load the application image:

```bash
kind load docker-image visitor-counter:v1 --name private
```

Apply Kubernetes configurations:

```bash
kubectl apply -f k8s/
```

Check deployments and pods:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

Access the application using port forwarding:

```bash
kubectl port-forward service/web 8081:80
```

Open:

```text
http://localhost:8081
```

## 🔍 Application Endpoints

| Endpoint | Description |
|---|---|
| `/` | Visitor counter interface |
| `/info` | Cluster and pod information |
| `/health` | Application liveness check |
| `/ready` | Redis connectivity check |
| `/work` | CPU-intensive workload for HPA testing |

## 📈 Kubernetes Autoscaling

The project uses Kubernetes Horizontal Pod Autoscaler (HPA).

| Configuration | Value |
|---|---|
| Minimum replicas | 2 |
| Maximum replicas | 6 |
| CPU utilization target | 50% |

Monitor autoscaling:

```bash
kubectl get hpa
kubectl get pods -w
```

The `/work` endpoint generates CPU-intensive activity to demonstrate scaling behavior.

## 🛡️ Health Monitoring & Self-Healing

- **Liveness Probe:** Checks whether the application is running.
- **Readiness Probe:** Checks whether Redis is reachable.
- **Self-Healing:** Kubernetes automatically replaces failed pods managed by the Deployment.

## 📸 Project Screenshots

Screenshots demonstrating the project implementation and deployment will be added here.

Planned evidence:

- Application dashboard
- Docker containers
- Kubernetes pods and services
- HPA autoscaling
- Self-healing and pod replacement
- Redis connectivity
- Health checks
- Final deployment verification

## 🎯 Learning Outcomes

- Containerization using Docker.
- Multi-container application deployment.
- Kubernetes Deployments and Services.
- Horizontal Pod Autoscaling.
- Resource requests and limits.
- Health probes and self-healing.
- Redis integration.
- Hybrid deployment and failover concepts.

## 👨‍💻 Author

**NIKHIL KUMAR**

B.Tech CSE | IILM University

GitHub: [@nikhil21z](https://github.com/nikhil21z)

Project Repository: [CloudComputingProject_](https://github.com/nikhil21z/CloudComputingProject_)

---

⭐ If you find this project useful, consider giving the repository a star!
