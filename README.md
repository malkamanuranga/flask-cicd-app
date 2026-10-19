<div align="center">

<!-- Animated Typing Header -->
<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=28&pause=1000&color=0D6EFD&center=true&vCenter=true&width=600&lines=Flask+CI%2FCD+Pipeline;Jenkins+%2B+Docker+%2B+Kubernetes;100%25+Local+Deployment;Zero+Cloud+Costs" alt="Typing SVG" />
</a>

<!-- Badges -->
![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=for-the-badge&logo=flask&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)

<p align="center">
  <b>A fully functional, locally hosted CI/CD pipeline showcasing the complete DevOps lifecycle.</b><br>
  From code commit ➔ automated testing ➔ containerization ➔ Kubernetes deployment.
</p>

</div>

---

## 📖 About The Project

This repository contains a complete, production-style **Flask Web Application** paired with an automated **CI/CD Pipeline**. It is designed to run entirely on a local machine (Windows/Mac/Linux) using Docker Desktop, requiring **zero cloud costs**. 

Whenever a developer pushes code to GitHub, Jenkins automatically detects the change, builds a new Docker image, runs a smoke test, and performs a rolling update on a local Kubernetes cluster.

### ✨ Key Features
*   🔐 **Secure Authentication:** Login, Signup, and Logout functionality using `Flask-Login` and hashed passwords.
*   🛡️ **Admin Panel:** Role-based access control to view all registered users.
*   📊 **Interactive Dashboard:** Beautiful, animated charts powered by `Chart.js`.
*   🐳 **Dockerized:** The app and the Jenkins server are fully containerized.
*   ⚙️ **Automated CI/CD:** Jenkins pipeline (`Jenkinsfile`) with automated builds and smoke tests.
*   ☸️ **Kubernetes Native:** Deployment manifests with self-healing and scaling capabilities.

---

## 🏗️ Architecture & Workflow

Here is how the magic happens. Every `git push` triggers a chain reaction:

```mermaid
graph TD
    A[👨‍💻 Developer Push] -->|git push| B(🐙 GitHub Repository)
    B -->|Poll SCM every 60s| C{🤖 Jenkins Pipeline}
    C -->|1. Checkout Code| D[🐳 Docker Build]
    D -->|2. Build Image| E[🧪 Smoke Test]
    E -->|3. curl /login| F{Pass?}
    F -->|Yes| G[☸️ Kubernetes Deploy]
    F -->|No| H[❌ Build Fails & Alerts]
    G -->|Rolling Update| I((🚀 App Live on Port 30080))
    
    style A fill:#0d6efd,color:#fff
    style B fill:#24292e,color:#fff
    style C fill:#d24939,color:#fff
    style G fill:#326ce5,color:#fff
    style I fill:#198754,color:#fff
🚀 Quick Start (Local Machine)
Prerequisites
Docker Desktop (with Kubernetes enabled)

Git

Kubectl (CLI)

1. Start Jenkins (The CI/CD Engine)
bash
cd jenkins-setup
docker compose up -d --build
Access Jenkins at http://localhost:8080

2. Run the App via Docker Compose (Optional - Local Testing)
If you just want to run the app without the pipeline:

bash
docker compose up -d
Access the app at http://localhost:5000

3. Default Credentials
Admin Username: admin

Admin Password: admin123

🧪 The CI/CD Pipeline Stages
The Jenkinsfile executes the following stages on every commit:

Stage	Description	Command Executed
1. Checkout	Pulls the latest code from GitHub.	git checkout
2. Build	Builds a new Docker image tagged with the build number.	docker build -t flask-cicd-app:${BUILD_NUMBER} .
3. Test	Spins up the container on a temp port and checks if the login page returns HTTP 200.	curl -f http://host.docker.internal:5055/login
4. Deploy	Updates the Kubernetes manifest and applies it to the cluster.	kubectl apply -f k8s/
☸️ Kubernetes Management Commands
Once deployed by Jenkins, you can manage your app using kubectl:

bash
# View the running pods (should be 2 replicas)
kubectl get pods

# Watch the rolling update happen in real-time
kubectl get pods -w

# Scale the app to 5 replicas manually
kubectl scale deployment flask-cicd-app --replicas=5

# Test self-healing (Kubernetes will instantly recreate it)
kubectl delete pod <pod-name-here>
<div align="center"> <p>Built with ❤️ for learning DevOps, CI/CD, and Kubernetes</p> <img src="https://forthebadge.com/images/badges/built-with-love.svg" /> <img src="https://forthebadge.com/images/badges/powered-by-coffee.svg" /> </div> ```