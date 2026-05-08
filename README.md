# DevOps for Cloud Computing

A collection of hands-on DevOps projects covering cloud deployment, containerization, CI/CD pipelines, container orchestration, and monitoring

---


## Projects

### 1. IaaS & PaaS Deployment — EC2 & Elastic Beanstalk

**Tech:** AWS EC2 · AWS Elastic Beanstalk · S3 · Docker · Docker Compose · Flask · MySQL

Demonstrates the two core cloud service models side by side:

- **IaaS:** Deployed a Flask + MySQL application on an AWS EC2 instance (Ubuntu, t3.micro) using Docker Compose. Configured Security Groups for HTTP/HTTPS/port 5000 and verified the live endpoint.
- **PaaS:** Re-deployed the same application to AWS Elastic Beanstalk with source code stored in S3. AWS automatically handled provisioning, load balancing, scaling, and health monitoring — zero manual server configuration required.

**Key concepts:** IaaS vs PaaS, Docker Compose, EC2 Security Groups, Elastic Beanstalk environments, S3 storage.

---

### 2. Docker Swarm Secrets Deployment

**Tech:** AWS EC2 · Docker · Docker Swarm · Docker Secrets · Node.js · MySQL

Deployed a Node.js + MySQL web application using Docker Swarm with secure secrets management:

- Initialized Docker Swarm on EC2, promoting the instance to a Swarm manager node.
- Created Docker Secrets for all database credentials (`db_user`, `db_password`, `db_name`, `mysql_root_password`) — eliminating plaintext environment variables entirely.
- Authored a `docker-stack.yml` defining web and db services with restart policies and a persistent named volume (`myapp_db_data`) for MySQL data durability.
- Built and pushed the Docker image to DockerHub; deployed the full stack with `docker stack deploy`.

**Key concepts:** Docker Swarm, secrets management, persistent volumes, stack deployment, DockerHub.

---

### 3. Jenkins CI/CD Pipeline with Docker & Selenium

**Tech:** AWS EC2 · Jenkins · Docker · Docker Compose · GitHub Webhooks · Selenium · pytest · Flask · MySQL

Built a complete CI/CD pipeline for a Flask To-Do web application:

- Configured a GitHub webhook to trigger Jenkins automatically on every push.
- Wrote a multi-stage `Jenkinsfile` with: code checkout, Python linting (Flake8 in Docker), Docker image build, unit tests (pytest), Selenium browser integration tests, artifact collection, and automated cleanup.
- Ran Selenium tests in a dedicated containerized test environment using headless Chrome.
- Resolved real-world pipeline issues including Flake8 formatting errors, port conflicts, and missing dependencies.

**Key concepts:** CI/CD, Jenkins pipelines, GitHub webhooks, Selenium testing, Docker Compose orchestration.

---

### 4. Kubernetes HPA & Prometheus/Grafana Monitoring

**Tech:** AWS EC2 · Kubernetes (Minikube) · Helm · Prometheus · Grafana · Docker · Flask · MySQL

Deployed a Flask notes application (PinkNotes) on Kubernetes with full observability:

- Authored Kubernetes manifests: `Deployment`, `Service (NodePort)`, `PersistentVolumeClaim`, and `HorizontalPodAutoscaler` (HPA scaling from 1–7 replicas based on memory utilization).
- Installed Prometheus and Grafana via Helm; configured real-time dashboards for CPU, memory, pod metrics, and network traffic.
- Generated synthetic load using a BusyBox pod to validate autoscaling behaviour and observe live metrics in Grafana.

**Key concepts:** Kubernetes, HPA, persistent storage, Helm, Prometheus, Grafana, observability.

---

### 5. MLOps — Malware Detector with Jenkins CI/CD

**Tech:** AWS EC2 · Jenkins · Docker · Docker Compose · Python · scikit-learn · GitHub

Built an ML-powered malware detection system with an automated CI/CD pipeline:

- Developed `train_model.py` to train a classification model on network logs, and `inference.py` to process logs and generate `alerts.csv`.
- Containerized the ML inference pipeline using Docker; composed multi-container setup with Docker Compose.
- Configured a Jenkins pipeline to automate model builds and deployments on every GitHub push.

**Key concepts:** MLOps, ML model containerization, Jenkins CI/CD, Docker, automated inference pipelines.

---

### 6. MLOps — Malware Detector on Kubernetes

**Tech:** AWS EC2 · Kubernetes (Minikube) · Docker · DockerHub · Python · scikit-learn

Extended the malware detector project with a full Kubernetes deployment:

- Containerized the trained ML model and pushed the image to DockerHub.
- Authored Kubernetes `Deployment`, `Service`, and `PersistentVolumeClaim` YAML manifests.
- Deployed the inference workload to Minikube on EC2 with persistent storage for model artifacts and output logs.

**Key concepts:** ML model deployment on Kubernetes, PVC, DockerHub, Minikube, inference workloads.

---

### 7. Full-Stack CI/CD Pipeline with Kubernetes & Monitoring

**Tech:** AWS EC2 · GitHub · Jenkins · Docker · Kubernetes (Minikube) · Prometheus · Grafana · Flask

The capstone final project — an end-to-end DevOps implementation for a Student Management & Attendance System:

- **Phase 1:** Developed a Flask web app on EC2 with full CRUD for students and attendance records.
- **Phase 2:** Set up GitHub version control with Personal Access Token authentication.
- **Phase 3:** Installed and configured Jenkins with GitHub SCM integration.
- **Phase 4:** Wrote a `Jenkinsfile` automating Docker image build, DockerHub push, and Kubernetes deployment across a single pipeline.
- **Phase 5:** Deployed to Kubernetes (Minikube) with `Deployment`, `Service (NodePort)`, and `PVC` manifests.
- **Phase 6:** Installed Prometheus and Grafana via Helm; imported Kubernetes dashboard (ID 315); monitored live CPU, memory, pod, and network metrics.

**Key concepts:** End-to-end DevOps, CI/CD, Kubernetes, Helm, monitoring, full pipeline automation.

---

## Tech Stack Overview

| Category | Tools |
|----------|-------|
| Cloud | AWS EC2, Elastic Beanstalk, S3 |
| Containers | Docker, Docker Compose, Docker Swarm |
| Orchestration | Kubernetes (Minikube), Helm |
| CI/CD | Jenkins, GitHub Webhooks |
| Monitoring | Prometheus, Grafana |
| Testing | pytest, Selenium, Flake8 |
| Languages | Python, Node.js, Bash |
| ML | scikit-learn, pandas, numpy |

---

## Author

**Zainab Qureshi**
