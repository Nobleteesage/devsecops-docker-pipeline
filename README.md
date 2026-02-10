# DevSecOps Docker CI/CD Pipeline

## 📌 Project Overview

This project demonstrates a **foundational DevSecOps CI/CD pipeline** using GitHub Actions, Docker, and container security scanning. The goal is to show how application code can be automatically built, containerized, security‑scanned, and pushed to Docker Hub using industry‑standard DevOps practices.

This repository represents the **initial phase** of a larger DevSecOps roadmap (Docker → Security → Kubernetes → Cloud).

---

## 🧱 What Has Been Implemented So Far

✔ GitHub repository with CI/CD automation
✔ Dockerized application
✔ GitHub Actions pipeline
✔ Automated Docker image build
✔ Docker Hub authentication via secrets
✔ Docker image push to Docker Hub
✔ Trivy container image vulnerability scanning

---

## 🛠️ Tech Stack

* **GitHub Actions** – CI/CD automation
* **Docker** – Containerization
* **Docker Hub** – Container image registry
* **Trivy** – Container image vulnerability scanning
* **Linux (Ubuntu runner)** – CI environment

---

## 📂 Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── ci-cd.yml
├── Dockerfile
├── README.md
└── application source files
```

---

## 🔄 CI/CD Pipeline Workflow

The pipeline is triggered automatically on every push to the `main` branch.

### Pipeline Stages

1. **Checkout Code**

   * Pulls the latest source code from the repository.

2. **Set Up Docker Buildx**

   * Prepares the GitHub runner for Docker image builds.

3. **Docker Image Build**

   * Builds the application image using the Dockerfile.

4. **Security Scan (Trivy)**

   * Scans the Docker image for known vulnerabilities.
   * Focuses on HIGH and CRITICAL severities.
   * Does not fail the pipeline (reporting‑only at this stage).

5. **Docker Hub Login**

   * Authenticates securely using GitHub Secrets.

6. **Push Docker Image**

   * Pushes the image to Docker Hub with the `latest` tag.

---

## 🔐 Secrets Management

Sensitive credentials are stored securely using **GitHub Actions Secrets**.

### Required Secrets

| Secret Name       | Description             |
| ----------------- | ----------------------- |
| `DOCKER_USERNAME` | Docker Hub username     |
| `DOCKER_PASSWORD` | Docker Hub access token |

> ⚠️ A Docker Hub **Access Token** is required (not your Docker Hub password).

---

## 🧪 Security Scanning (Trivy)

Trivy is used to scan the Docker image for vulnerabilities during the CI pipeline.

* Detects OS and application‑level vulnerabilities
* Reports HIGH and CRITICAL issues
* Can later be configured to **fail the pipeline** for stricter security

This provides early visibility into security risks before deployment.

---

## 🐳 Docker Hub Output

After a successful pipeline run, the Docker image is available at:

```
docker.io/<docker-username>/devsecops-app:latest
```

The presence of the `latest` tag confirms:

* Successful build
* Successful authentication
* Successful push from CI

---

## 🚀 How to Run Locally

```bash
docker pull <docker-username>/devsecops-app:latest
docker run -p 5000:5000 <docker-username>/devsecops-app:latest
```

---

## 🧭 DevSecOps Roadmap (Next Phases)

This project is intentionally built in phases.

### Phase 2 – Advanced Security

* Snyk dependency scanning
* OWASP Dependency‑Check
* Pipeline enforcement on vulnerabilities

### Phase 3 – Kubernetes

* Kubernetes deployment manifests
* Helm charts
* Image scanning in K8s

### Phase 4 – Cloud & IaC

* Terraform infrastructure provisioning
* Cloud deployment (AWS / Azure / GCP)
* Secure secrets management

---

## 🎯 Learning Objectives

* Understand CI/CD pipeline structure
* Learn Docker image automation
* Apply security scanning early (shift‑left security)
* Build real‑world DevSecOps troubleshooting skills

---

## ⚠️ Known Issues & Lessons Learned

### Known Issues Encountered

* Docker image push failures due to incorrect secret configuration
* Docker Hub authentication errors caused by using passwords instead of access tokens
* CI/CD pipeline failures caused by missing or misordered Docker setup steps
* Confusion between GitHub Actions runners and self-hosted runners

These issues were resolved through iterative debugging and pipeline refactoring.

---

### Lessons Learned

* CI/CD pipelines only execute when triggered (push, PR, or manual run)
* Docker Hub requires **access tokens**, not account passwords, for CI authentication
* Small misconfigurations in YAML files can cascade into multiple pipeline failures
* Separating pipeline stages improves debuggability and stability
* DevSecOps work involves continuous troubleshooting, not just initial setup

---

## 📎 Notes

This repository focuses on **learning and implementation clarity**, not production hardening. Each phase builds on a stable foundation.

---

## 👤 Author

GORIOLA-OBAFEMI BABATUNDE SUKANMI
DevSecOps / Cloud Engineering Practice Project

