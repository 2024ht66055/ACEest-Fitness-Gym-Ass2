# 🏋️ ACEest Fitness & Gym – DevOps Project
---

## 📖 Table of Contents
- [Project Overview](#-project-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
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
| Deployment       | Kubernetes               |

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

## Docker HUB Respository
<img width="1873" height="702" alt="image" src="https://github.com/user-attachments/assets/43bb539b-5a21-462e-82b3-154c18dc9334" />


---

## <img width="48" height="48" alt="icons8-git-48" src="https://github.com/user-attachments/assets/ed9baf75-2723-45a3-af7f-195e42edc098" /> GIT RESPOSITORY


<img width="1128" height="586" alt="image" src="https://github.com/user-attachments/assets/7c22651c-0105-4c45-8f0d-f5e7a87727be" />
---
<img width="1334" height="469" alt="image" src="https://github.com/user-attachments/assets/bef4f0a7-d01e-4b45-aee6-3d954d851d16" />
---
<img width="1128" height="515" alt="image" src="https://github.com/user-attachments/assets/7b2199db-0e0f-47f6-aeaa-b62034b7c756" />


## <img width="50" height="50" alt="icons8-jenkins-50" src="https://github.com/user-attachments/assets/0efc2d42-f73a-41f4-a2ee-6da615ee7e54" /> JENKINS OUTPUT TAKEN FROM CLOUD VM

<img width="1891" height="658" alt="image" src="https://github.com/user-attachments/assets/2b4c2f05-9852-4b0a-afd9-bcdaa87a3e33" />

## Docker Token Access
<img width="1320" height="486" alt="image" src="https://github.com/user-attachments/assets/11e8f73f-1b88-454f-aa14-fe3d97143f51" />

## Automate Build after every update(2 mins)
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


<img width="1329" height="308" alt="image" src="https://github.com/user-attachments/assets/7ebb2f22-0027-40a3-af5c-c3a9c6918358" />




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

## 👻 Shadow Deployment

## Create Shadow Yaml File
<img width="980" height="546" alt="image" src="https://github.com/user-attachments/assets/ce10dd57-758e-4c24-9b80-f14ff7fad116" />

## Create service.yaml
<img width="1176" height="479" alt="image" src="https://github.com/user-attachments/assets/ebdce42a-5341-4b8c-920c-59ac244209bc" />

## Shadow pods Running
<img width="841" height="203" alt="image" src="https://github.com/user-attachments/assets/540b7bc8-3c71-4e69-a2c9-0d546e392248" />

## Shadow Received traffic (GET REquests)
<img width="840" height="434" alt="image" src="https://github.com/user-attachments/assets/889ae808-5086-4773-ad4b-446bc41148c7" />

## 👥 A/B Testing

## A/B Deployments
<img width="564" height="212" alt="image" src="https://github.com/user-attachments/assets/bea62f56-d72c-4a3e-9eaf-68cfbb7b0e1b" />

## A/B Pods with labels
<img width="824" height="106" alt="image" src="https://github.com/user-attachments/assets/b46a758f-dd86-42b9-b12b-8b185c7d71f4" />

## A/B service
<img width="611" height="114" alt="image" src="https://github.com/user-attachments/assets/a51b80d6-154a-49ba-a0e3-d6c9e8715bfa" />

## A/B Endpoints
<img width="613" height="74" alt="image" src="https://github.com/user-attachments/assets/7dac541c-0772-410a-9286-d9633bbda840" />

## Two sepearte A/B deployments created
<img width="826" height="79" alt="image" src="https://github.com/user-attachments/assets/cf1b5934-361f-4e35-8fa4-aeaf15826cac" />

<img width="835" height="101" alt="image" src="https://github.com/user-attachments/assets/298df5cd-6346-46db-9910-51afbafbf697" />

## A/B Kubernetes Deploy
<img width="1354" height="527" alt="image" src="https://github.com/user-attachments/assets/0d61079b-3018-41cc-81fa-52dd4f067992" />

## 🔁 Rolling Update
<img width="495" height="82" alt="image" src="https://github.com/user-attachments/assets/bf9668a8-1500-4206-a9ad-8100c6956047" />

## Rolling Kubernetes Deploy
<img width="1277" height="459" alt="image" src="https://github.com/user-attachments/assets/3eab12c6-2392-4413-be96-64f37aa7f901" />

## Old pods terminating & New pods creating
<img width="781" height="192" alt="image" src="https://github.com/user-attachments/assets/160f7626-7c14-4a15-a1de-3e1172a46816" />

##  Version 2
<img width="789" height="79" alt="image" src="https://github.com/user-attachments/assets/3096d8ac-8631-44b8-978d-9172b8941492" />

## Rollback to Version 1
<img width="813" height="359" alt="image" src="https://github.com/user-attachments/assets/714c54c6-f698-456b-a439-232fcec2f78f" />

## Automate Build & Test Output from CLOUD VM

## Jenkins Pipeline Stages
<img width="1598" height="646" alt="image" src="https://github.com/user-attachments/assets/121b8639-ef0e-44f2-9ed7-8a8560edf1f6" />

## Pytest Output
<img width="738" height="473" alt="image" src="https://github.com/user-attachments/assets/5de349a6-b4fa-4ddb-ade1-640845d16a74" />

## SonarQube Output
<img width="1749" height="928" alt="image" src="https://github.com/user-attachments/assets/406b499c-988d-4424-b08d-f336db53aa4c" />
<img width="1750" height="794" alt="image" src="https://github.com/user-attachments/assets/e93cb7f8-7c3b-4df3-958c-1c337826fd55" />
<img width="1695" height="824" alt="image" src="https://github.com/user-attachments/assets/01266523-81fa-4f4c-bdea-bd2e48f7d7bf" />
<img width="1647" height="782" alt="image" src="https://github.com/user-attachments/assets/eeb4e29c-5a5e-4e60-8885-0cdb96ad00ad" />



## SonarQube Docker Image
<img width="1346" height="451" alt="image" src="https://github.com/user-attachments/assets/78a9e81b-82f5-42b1-9683-77615ee2586b" />



## 🔁 DevOps Workflow Summary

```
Developer Code 
   ↓
GitHub Repository (Version Control)
   ↓
GitHub Actions (Optional CI: Lint + Initial Tests)
   ↓
Jenkins Pipeline (Automated CI/CD)
   ├── Checkout Code
   ├── Build Docker Image
   ├── Run Pytest (Unit Testing)
   ├── SonarQube Analysis (Code Quality + Quality Gate)
   ├── Push Docker Image to Docker Hub (Versioned)
   ↓
Kubernetes Deployment (CD Phase)
   ├── Blue-Green Deployment
   ├── Canary Release
   ├── Shadow Deployment
   ├── A/B Testing
   ├── Rolling Updates
   ↓
Rollback Mechanism (if failure occurs)
   ↓
Verified & Stable Application
```
---


## 📌 Key DevOps Concepts Demonstrated

* Version Control with Git
* Continuous Integration (CI)
* Continuous Deployment (CD)
* Automated Testing (Pytest)
* Containerization using Docker
* Container Orchestration using Kubernetes
* Deployment Strategies (Blue-Green, Canary, Shadow, A/B Testing, Rolling Updates)
* Rollback and Failure Recovery Mechanisms
* Pipeline Automation (Jenkins & GitHub Actions)
* Infrastructure as Code (YAML-based configuration)
* Environment Consistency across deployments
* Code Quality Analysis using SonarQube
* Basic Monitoring and Logging


---

## ⚠️ Notes

* SQLite database is created locally on first run
* Database file is excluded using `.gitignore`
* Docker container uses an isolated environment
* No production deployment included (development-focused project)
* Kubernetes is used for orchestrating containerized deployments and managing application lifecycle
* CI/CD integration is demonstrated using Jenkins, along with automated testing and code quality analysis.

---

## 👨‍💻 Author

* Rupesh Naik - 2024HT66055
* Developed as part of a DevOps learning assignment.

---

## 🎯 Conclusion

The project successfully demonstrates the implementation of modern deployment strategies and CI/CD practices using Kubernetes and supporting tools. Various deployment techniques including Blue-Green, Canary, Shadow, A/B Testing, and Rolling Updates were implemented and analyzed to understand their behavior in real-world scenarios.
Kubernetes played a crucial role in managing containerized applications, enabling seamless updates, scalability, and high availability. The rollback mechanism ensured system reliability by allowing quick recovery to a stable version in case of failures.
Furthermore, the integration of Jenkins pipelines automated the build, testing, and deployment processes, while Pytest ensured functional validation of the application. SonarQube enhanced code quality through static analysis and quality gate enforcement.
Overall, the project highlights how DevOps practices and Kubernetes-based deployment strategies can improve software delivery efficiency, reduce downtime, and maintain system stability. This implementation provides a strong foundation for scalable and reliable application deployment in production environments.

---
