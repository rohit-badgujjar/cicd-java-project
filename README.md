# 🚀 Ultimate Java CI/CD Pipeline using Jenkins, Docker, Kubernetes & Argo CD


## 📌 Project Overview

This project demonstrates an **end-to-end CI/CD pipeline** for a **Spring Boot Java application**.

The objective of this project was to automate the entire software delivery lifecycle—from source code commit to deployment on Kubernetes—using modern DevOps tools.

### CI Tool
- Jenkins

### CD Tool
- Argo CD (GitOps)

Whenever a developer pushes code to GitHub, the pipeline automatically:

1. Triggers Jenkins using GitHub Webhook
2. Checks out the latest source code
3. Builds the application using Maven
4. Runs tests
5. Performs Static Code Analysis using SonarQube
6. Builds a Docker image
7. Pushes the Docker image to Docker Hub
8. Updates the Kubernetes Deployment manifest with the latest image tag
9. Pushes the updated manifest to GitHub
10. Argo CD detects the manifest change and automatically syncs the Kubernetes cluster
11. The latest application becomes available without any manual deployment

---

# 🏗️ CI/CD Architecture

The complete workflow is shown below.

![CI/CD Architecture](java-project-complete-cicd-setup/images/Project-Architecture.png)

---

# 🛠️ Tech Stack

| Category | Technology |
|----------|------------|
| Language | Java |
| Framework | Spring Boot |
| Build Tool | Maven |
| CI | Jenkins |
| Code Quality | SonarQube |
| Containerization | Docker |
| Container Registry | Docker Hub |
| Orchestration | Kubernetes |
| GitOps CD | Argo CD |
| Source Control | Git & GitHub |
| Operating System | Ubuntu (EC2) |
| Cloud | AWS EC2 |

---

# 📂 Repository Structure

```
java-project-complete-cicd-setup/
│
├── spring-boot-app/
│   ├── src/
│   ├── pom.xml
│   └── Dockerfile
│
├── spring-boot-app-manifests/
│   ├── deployment.yml
│   ├── service.yml
│   └── namespace.yml
│
├── Jenkinsfile
│
└── README.md
```

---

# ⚙️ CI/CD Workflow

```
Developer
     │
     ▼
GitHub Push
     │
     ▼
GitHub Webhook
     │
     ▼
Jenkins Pipeline
     │
     ├── Checkout
     ├── Maven Build
     ├── Unit Tests
     ├── SonarQube Analysis
     ├── Docker Build
     ├── Docker Push
     └── Update Kubernetes Manifest
                │
                ▼
          Push Manifest
                │
                ▼
             GitHub
                │
                ▼
            Argo CD
                │
                ▼
        Kubernetes Cluster
                │
                ▼
      Updated Spring Boot App
```

---

# 🔄 Jenkins Pipeline Stages

The Jenkins pipeline consists of the following stages:

- Checkout SCM
- Checkout Source Code
- Build Application
- Run Tests
- Verify Agent
- Static Code Analysis (SonarQube)
- Build Docker Image
- Push Docker Image to Docker Hub
- Update Deployment Manifest
- Push Updated Manifest to GitHub

---

# ☁️ Deployment Strategy

Instead of directly deploying from Jenkins to Kubernetes, this project follows the **GitOps approach**.

Jenkins only updates the Kubernetes deployment manifest with the latest Docker image tag.

Example:

```yaml
image: username/spring-boot-app:9
```

Once this manifest is committed and pushed to GitHub, Argo CD automatically detects the change and synchronizes the Kubernetes cluster.

This approach ensures:

- Version-controlled deployments
- Automatic synchronization
- Easy rollback
- Better audit history
- Git as the single source of truth

---

# 📸 Project Results

## 1. Jenkins Pipeline Successful

The complete Jenkins CI pipeline executed successfully.

![Jenkins Pipeline](java-project-complete-cicd-setup/images/Jenkins-passed-stages.png)

---

## 2. Argo CD Successfully Synced

Argo CD automatically synchronized the latest deployment after Jenkins updated the Kubernetes manifest.

![Argo CD](java-project-complete-cicd-setup/images/argocd-deployed-app.png)

---

## 3. Spring Boot Application Running

The deployed application is successfully running inside the Kubernetes cluster and is accessible through the exposed service.

![Spring Boot Application](java-project-complete-cicd-setup/images/deployed-app.jpeg)

---

# 📦 Docker Image

The pipeline automatically builds and pushes Docker images to Docker Hub with incrementing Jenkins build numbers.

Example:

```
username/spring-boot-app:1
username/spring-boot-app:2
username/spring-boot-app:3
...
username/spring-boot-app:9
```

---

# ⭐ Features

- Fully Automated CI/CD Pipeline
- GitHub Webhook Integration
- Maven Build Automation
- Automated Testing
- SonarQube Static Code Analysis
- Docker Image Build & Push
- GitOps Deployment
- Kubernetes Deployment
- Automatic Argo CD Synchronization
- Version Controlled Kubernetes Manifests

---



---

