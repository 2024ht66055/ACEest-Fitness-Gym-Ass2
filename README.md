# 🏋️ ACEest Fitness & Gym – DevOps Project
---

## 📖 Table of Contents
- [Project Overview](#-project-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Screenshots](#-screenshots)
- [Conclusion](#-conclusion)

---

## 🚀 Project Overview

This project implements a complete DevOps CI/CD pipeline for the ACEest Fitness & Gym Management System, a Flask-based application for managing gym clients and workouts.

The application is developed in multiple versions and automated using GitHub (version control), Jenkins (CI), Pytest (testing), SonarQube (code quality), Docker (containerization), and Kubernetes (deployment).

The pipeline ensures continuous integration, automated testing, and reliable deployment through containerized environments. Advanced deployment strategies such as Rolling Updates, Blue-Green Deployment, Canary Release, and Rollback mechanisms are used to achieve zero-downtime and safe releases.

Overall, the project demonstrates how DevOps practices enhance automation, code quality, scalability, and deployment reliability in a real-world scenario.

---

## 🧩 Features

### 🔐 Authentication

* Simple login system
* Default admin user:

  * Username: `admin`
  * Password: `admin`

### 👤 Client Management

* Add new clients
* View all clients
* Store membership status

### 🧠 Program Generation

* Automatically generate fitness programs
* Randomized based on predefined templates

### 🏋️ Workout Management

* Add workouts for clients
* View workout history
* Track duration and notes

### 🗄️ Database

* SQLite database (`aceest_fitness.db`)
* Automatically initialized

### ⚙️ DevOps & Deployment
* Version control using Git & GitHub
* CI pipeline using Jenkins
* Automated testing with Pytest
* Code quality analysis using SonarQube
* Docker-based containerization
* Image versioning using Docker Hub
* Kubernetes-based deployment
---

## 🛠 Tech Stack

| Component        | Technology               |
| ---------------- | ------------------------ |
| Backend          | Flask (Python)           |
| Database         | SQLite                   |
| Testing          | Pytest                   |
| Containerization | Docker                   |
| CI/CD            | Jenkins + GitHub Actions |
| Version Control  | Git & GitHub             |
| Code Quality     | SoanrQube                |
| Container Regis  | Docker Hub               |
| Orchestr&Deploy  | Kubernetes               |

---

## 📁 Project Structure
```
2024HT66055ASS2/
│
├── appv1.py                 # Version 1 of Flask application
├── appv2.py                 # Stable version (used in deployments)
├── appv3.py                 # Updated version (used for canary/green)
│
├── aceest_fitness.db        # SQLite database
├── requirements.txt         # Python dependencies
├── README.md                # Project documentation
├── .gitignore               # Ignored files
│
├── Dockerfile               # Main Docker configuration
├── dockerfileblue           # Dockerfile for Blue version
├── dockerfilegreen          # Dockerfile for Green version
│
├── Jenkinsfile              # Jenkins CI/CD pipeline
│
├── deployment.yaml          # Base Kubernetes deployment
├── service.yaml             # Kubernetes service (NodePort)
│
├── blue-deployment.yaml     # Blue environment deployment
├── blueservice.yaml         # Blue service configuration
│
├── green-deployment.yaml    # Green environment deployment
├── greenservice.yaml        # Green service configuration
│
├── myapp/                   # Additional deployment configs
│   ├── canary.yaml          # Canary deployment
│   ├── stable.yaml          # Stable deployment
│   ├── service.yaml         # Shared service
│   ├── shadow.yaml          # Shadow deployment
│   ├── shservice.yaml       # Shadow service
│
├── tests/                   # Test cases
│   └── test_app.py          # Pytest tests
│
└── .github/
    └── workflows/
        └── main.yml         # GitHub Actions CI workflow
```

---

## ⚙️ Local Setup & Execution

### 1️⃣ Clone the repository

```bash
git clone https://github.com/2024ht66055/ACEest-Fitness-Gym-Ass2.git
cd ACEest-Fitness-Gym-Ass2
```

### 2️⃣ Install dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Run the application

```bash
python appv1.py
```

### 4️⃣ Open in browser

```
http://127.0.0.1:5000/
```

---
## <img width="51" height="51" alt="history (3)" src="https://github.com/user-attachments/assets/34e9a68a-5633-43ba-9330-f649aa560322" />Version Control

Multiple versions (v1, v2, v3) are managed using commits and tags

## 🧪 Running Tests (Pytest)

Run all tests using:

```bash
pytest
```

Tests include:

* Home route validation
* Database initialization
* Login functionality
* Error handling

---

## 🐳 Docker Setup

### Build Docker Image

```bash
docker build -t 2024ht66055/appv2:v2 .
docker build -t 2024ht66055/appv2:v3 .
```

### Run Container

```bash
docker run -p 5000:5000 2024ht66055/appv2:v2
docker run -p 5000:5000 2024ht66055/appv2:v3
```

### Run Tests Inside Docker

```bash
docker run --rm 2024ht66055/appv2:v2 pytest
docker run --rm 2024ht66055/appv2:v3 pytest
```
### Docker Hub push
```bash
docker push 2024ht66055/appv2:v2
docker push 2024ht66055/appv2:v3
```
---

## ⚙️ Jenkins Pipeline

The Jenkins pipeline automates the build process.

### Pipeline Stages:

1. **Checkout Code**

   * Pulls code from GitHub

2. **Build Docker Image**

   * Creates containerized environment

3. **Run Tests**

   * Executes Pytest inside Docker
  
 4. **Code Quality Analysis (SonarQube)**

   * Performs static code analysis

 5. **Docker Image Push**

   * Authenticates using Jenkins credentials

 6. **Deployment to Kubernetes**

   * Deploys application using Kubernetes manifests


### Outcome:

* Automated build and testing
* Ensures code quality (SonarQube)
* Reliable containerized deployment
* Supports multiple deployment strategies
* Acts as a quality gate before deployment

---

## 🔄 GitHub Actions CI/CD

GitHub Actions automates testing on every code change.

### Trigger Conditions:

* On every `push`
* On every `pull_request`

### Workflow Steps:

1. Checkout repository
2. Setup Python environment
3. Install dependencies
4. Run Pytest
5. Build Docker image

### Result:

* Automatic validation of every change
* Prevents broken code from entering main branch

---
## <img width="40" height="40" alt="icons8-kubernetes-48" src="https://github.com/user-attachments/assets/a87b453b-0ab4-40e9-a15b-eb8f0d4cb8da" /> Kubernetes

* The application is deployed using Kubernetes

## 🚀 Implemented Deployment Strategies

* Rolling Updates
* Blue-Green Deployment
* Canary Release
* Rollback
* Shadow Deployment
* A/B Testing
## 📸 Screenshots

Below Windows shows different activities done to complete the assignment.


## ACest-Fitness-Gym TESTING PAGE

*	Local setup and execution instructions.

<img width="903" height="488" alt="image" src="https://github.com/user-attachments/assets/6da60c72-8534-46ad-9151-94d298443260" />

<img width="391" height="365" alt="image" src="https://github.com/user-attachments/assets/938b867e-d20f-4ed4-b64e-31779ffb1dbf" />

<img width="479" height="493" alt="image" src="https://github.com/user-attachments/assets/c77401eb-340c-439a-8ef2-d0d584746c54" />

## <img width="32" height="32" alt="pytest-original-32px" src="https://github.com/user-attachments/assets/8a56976d-cbf6-43a2-a964-378ac692ffa4" /> PYTEST
<img width="1003" height="370" alt="image" src="https://github.com/user-attachments/assets/8b9cbc79-1bef-4141-bef5-c8d85461f5a8" />

## <img width="48" height="48" alt="icons8-docker-48" src="https://github.com/user-attachments/assets/07964fed-5d45-4bdc-9143-77485723ce33" /> DOCKER TEST

![1](https://github.com/user-attachments/assets/03dd006a-71e2-471b-8770-24b18c4a2bde)

![2](https://github.com/user-attachments/assets/cc0dca67-fcdc-4b90-aa8b-d2ceec2357b5)

![3](https://github.com/user-attachments/assets/72f35d2c-f677-44eb-82a0-e94faf23dff3)

![4](https://github.com/user-attachments/assets/069781dc-75ae-4237-9a15-fd56ecbd9291)





---

## <img width="48" height="48" alt="icons8-git-48" src="https://github.com/user-attachments/assets/ed9baf75-2723-45a3-af7f-195e42edc098" /> GIT RESPOSITORY


<img width="1128" height="586" alt="image" src="https://github.com/user-attachments/assets/7c22651c-0105-4c45-8f0d-f5e7a87727be" />
---
<img width="1334" height="469" alt="image" src="https://github.com/user-attachments/assets/bef4f0a7-d01e-4b45-aee6-3d954d851d16" />
---
<img width="1128" height="515" alt="image" src="https://github.com/user-attachments/assets/7b2199db-0e0f-47f6-aeaa-b62034b7c756" />


## <img width="50" height="50" alt="icons8-jenkins-50" src="https://github.com/user-attachments/assets/0efc2d42-f73a-41f4-a2ee-6da615ee7e54" /> JENKINS

<img width="1348" height="454" alt="image" src="https://github.com/user-attachments/assets/a618f8c2-53f1-4899-beb3-826ec3a06910" />

<img width="1630" height="731" alt="1" src="https://github.com/user-attachments/assets/ce4fd9a0-99cd-4899-91a8-3a616daddd9f" />

<img width="1172" height="419" alt="image" src="https://github.com/user-attachments/assets/5ea63ed3-35a0-4f51-9bf8-9295c65bb0fe" />

<img width="1520" height="604" alt="2" src="https://github.com/user-attachments/assets/cafd5529-7265-4bea-ad3d-47f18e7440e8" />

<img width="1281" height="551" alt="image" src="https://github.com/user-attachments/assets/80f1d1e8-8e14-420e-a862-26059a24ff28" />

<img width="1280" height="516" alt="image" src="https://github.com/user-attachments/assets/2f8033ae-ca1a-44c6-be4e-9560909f94c5" />

<img width="1172" height="508" alt="image" src="https://github.com/user-attachments/assets/168b3258-0a57-4724-94b1-cbe7e7b3ad55" />

<img width="1011" height="292" alt="image" src="https://github.com/user-attachments/assets/89634ad1-5c20-43c6-86e6-9145fe71a41d" />



## <img width="48" height="48" alt="icons8-git-48" src="https://github.com/user-attachments/assets/ed9baf75-2723-45a3-af7f-195e42edc098" /> Github Actions

<img width="987" height="456" alt="image" src="https://github.com/user-attachments/assets/4b18ef2b-c38e-40b6-b403-54209942eb9c" />

<img width="1016" height="515" alt="image" src="https://github.com/user-attachments/assets/a96f6bb9-9a1a-4dbc-a652-c4ff4b6843f9" />



## 🔁 DevOps Workflow Summary

```
Developer Code → GitHub → GitHub Actions (Test + Build)
                    ↓
                 Jenkins (Build + Test in Docker)
                    ↓
               Verified Application
```
---


## 📌 Key DevOps Concepts Demonstrated

* Version Control with Git
* Continuous Integration (CI)
* Automated Testing
* Containerization (Docker)
* Pipeline Automation (Jenkins & GitHub Actions)
* Environment Consistency

---

## ⚠️ Notes

* SQLite database is created locally on first run
* Database file is excluded using `.gitignore`
* Docker container uses an isolated environment
* No production deployment included (development-focused project)

---

## 👨‍💻 Author

* Rupesh Naik - 2024HT66055
* Developed as part of a DevOps learning assignment.

---

## 🎯 Conclusion

This project demonstrates how a simple Python application can be transformed into a **production-ready, automated pipeline-driven system** using modern DevOps tools.

It ensures:

* Code reliability
* Faster development cycles
* Automated validation
* Environment consistency

---
