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

## ⚙️ Setup & Execution

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

## <img width="30" height="30" alt="icons8-kubernetes-48" src="https://github.com/user-attachments/assets/a87b453b-0ab4-40e9-a15b-eb8f0d4cb8da" /> Kubernetes

* The application is deployed using Kubernetes

## 🚀 Implemented Deployment Strategies

* Rolling Updates
* Blue-Green Deployment
* Canary Release
* Rollback
* Shadow Deployment
* A/B Testing

---
## <img width="30" height="30" alt="icons8-testing-30" src="https://github.com/user-attachments/assets/1d3c26aa-c565-4414-a73e-13e5f29bd744" /> Automated Testing & Quality Assurance

* Unit tests implemented using Pytest
* Tests executed:During GitHub Actions&Inside Docker container
* SonarQube used for static code analysis

## 📸 Screenshots

Below Windows shows different activities done to complete the assignment.


## ACest-Fitness-Gym TESTING PAGE

*	Local setup and execution instructions.

<img width="903" height="488" alt="image" src="https://github.com/user-attachments/assets/6da60c72-8534-46ad-9151-94d298443260" />

<img width="391" height="365" alt="image" src="https://github.com/user-attachments/assets/938b867e-d20f-4ed4-b64e-31779ffb1dbf" />

<img width="479" height="493" alt="image" src="https://github.com/user-attachments/assets/c77401eb-340c-439a-8ef2-d0d584746c54" />

## <img width="32" height="32" alt="pytest-original-32px" src="https://github.com/user-attachments/assets/8a56976d-cbf6-43a2-a964-378ac692ffa4" /> PYTEST Different Version Files
<img width="829" height="569" alt="image" src="https://github.com/user-attachments/assets/fbd4a29e-d303-41d4-b6f9-5a89c6911b53" />


## <img width="48" height="48" alt="icons8-docker-48" src="https://github.com/user-attachments/assets/07964fed-5d45-4bdc-9143-77485723ce33" /> DOCKER TEST

![1](https://github.com/user-attachments/assets/03dd006a-71e2-471b-8770-24b18c4a2bde)

<img width="1356" height="593" alt="image" src="https://github.com/user-attachments/assets/230f327f-be4d-4df6-a0c7-93221433dc2e" />

<img width="1342" height="586" alt="image" src="https://github.com/user-attachments/assets/2e55eb18-e6ac-41d5-a254-21f361c52070" />

<img width="1320" height="580" alt="image" src="https://github.com/user-attachments/assets/3189a603-8a57-43b2-97f0-6cdb1ee5efa8" />


---

## <img width="48" height="48" alt="icons8-git-48" src="https://github.com/user-attachments/assets/ed9baf75-2723-45a3-af7f-195e42edc098" /> GIT RESPOSITORY


<img width="1128" height="586" alt="image" src="https://github.com/user-attachments/assets/7c22651c-0105-4c45-8f0d-f5e7a87727be" />
---
<img width="1334" height="469" alt="image" src="https://github.com/user-attachments/assets/bef4f0a7-d01e-4b45-aee6-3d954d851d16" />
---
<img width="1128" height="515" alt="image" src="https://github.com/user-attachments/assets/7b2199db-0e0f-47f6-aeaa-b62034b7c756" />


## <img width="50" height="50" alt="icons8-jenkins-50" src="https://github.com/user-attachments/assets/0efc2d42-f73a-41f4-a2ee-6da615ee7e54" /> JENKINS

<img width="1891" height="658" alt="image" src="https://github.com/user-attachments/assets/2b4c2f05-9852-4b0a-afd9-bcdaa87a3e33" />

## Docker Token Access
<img width="1320" height="486" alt="image" src="https://github.com/user-attachments/assets/11e8f73f-1b88-454f-aa14-fe3d97143f51" />

## Automate Build after every update(2 secs)
<img width="1749" height="638" alt="image" src="https://github.com/user-attachments/assets/a5f0eb89-4a6e-4015-aada-a7baa7696330" />

## Build Artifacts
<img width="792" height="590" alt="image" src="https://github.com/user-attachments/assets/d03a391c-5f83-4436-896c-e0d3969d1d9e" />


## Build success
<img width="846" height="729" alt="image" src="https://github.com/user-attachments/assets/d9103a1e-1111-43dd-9049-a2057623c92d" />

## Console Output
<img width="841" height="739" alt="image" src="https://github.com/user-attachments/assets/07c5b599-bec8-4220-84d9-4a1a67d09e37" />

<img width="839" height="481" alt="image" src="https://github.com/user-attachments/assets/cf64a86d-eb9f-4208-afd8-f6be735f171d" />

<img width="858" height="750" alt="image" src="https://github.com/user-attachments/assets/8c1fa8de-b969-4b61-95b3-c9d77f681e41" />

## Pipeline Steps
<img width="1621" height="751" alt="image" src="https://github.com/user-attachments/assets/d55f970d-571b-4d30-b6b8-5a199cc06ca1" />

## SonarQube Token Access
<img width="1726" height="670" alt="image" src="https://github.com/user-attachments/assets/17e416de-4bdb-40a1-88cb-94bf52420a52" />


<img width="1011" height="292" alt="image" src="https://github.com/user-attachments/assets/89634ad1-5c20-43c6-86e6-9145fe71a41d" />



## <img width="48" height="48" alt="icons8-git-48" src="https://github.com/user-attachments/assets/ed9baf75-2723-45a3-af7f-195e42edc098" /> Github Actions

<img width="1336" height="555" alt="image" src="https://github.com/user-attachments/assets/707b8589-751e-443b-8d0f-1b8b9f7954da" />


<img width="1354" height="588" alt="image" src="https://github.com/user-attachments/assets/37dfd25a-53e4-4e2b-8515-c79beb0ee9ea" />

## <img width="30" height="30" alt="icons8-kubernetes-48" src="https://github.com/user-attachments/assets/a87b453b-0ab4-40e9-a15b-eb8f0d4cb8da" />Kubernetes

## Kubetl Deployments
<img width="1359" height="605" alt="image" src="https://github.com/user-attachments/assets/f0a0650e-8db9-4760-8878-2ed17ac660f7" />

## Kubetl Pods
<img width="828" height="412" alt="image" src="https://github.com/user-attachments/assets/24089919-bd47-4235-a865-e3103303296c" />

## Rollback Blue-Green Deployment

## Green version

<img width="855" height="429" alt="image" src="https://github.com/user-attachments/assets/13ba083e-4434-47ff-a1af-c5e229a3f5a8" />

## Stimulate Failure
<img width="720" height="298" alt="image" src="https://github.com/user-attachments/assets/60a30a62-436b-4efb-b268-bfc2ac370543" />

## Green Website not loading
<img width="1306" height="540" alt="image" src="https://github.com/user-attachments/assets/26112bb0-8db2-4e80-a2c4-951b9080eec9" />

## Rollback to Blue
<img width="647" height="122" alt="image" src="https://github.com/user-attachments/assets/25b372b4-dc31-492c-b436-5abd73335502" />

## Blue Website loading
<img width="838" height="373" alt="image" src="https://github.com/user-attachments/assets/7c3dc1f9-485f-4008-84a4-df27c35ed519" />


## <img width="60" height="60" alt="image" src="https://github.com/user-attachments/assets/98ca7d57-1163-40dc-9cfa-fc9e3f82822e" />Canary Release

## Canary Release Deployment
<img width="791" height="211" alt="image" src="https://github.com/user-attachments/assets/a388a811-22d7-4a4f-8a00-3ff364e8e545" />

## Balance Traffic in Canary Release - V1(75%) & V2(25%)
<img width="801" height="216" alt="image" src="https://github.com/user-attachments/assets/b913876c-eab7-4dd3-88aa-a9045f0f956c" />



 








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
