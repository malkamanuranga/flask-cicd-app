```markdown
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d6efd,100:326ce5&height=200&section=header&text=Flask%20CI/CD%20Pipeline&fontSize=50&fontAlignY=35&desc=End-to-End%20DevOps%20Automation%20%7C%20Zero%20Cloud%20Costs&descAlignY=55&descSize=20&fontColor=ffffff" width="100%" />

<div align="center">

<a href="https://git.io/typing-svg">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=24&pause=1000&color=0D6EFD&center=true&vCenter=true&width=600&lines=Welcome+to+the+Full+DevOps+Lifecycle;Automated+Testing+%2B+Docker+Builds;Kubernetes+Deployments;100%25+Local+Machine+Setup" alt="Typing SVG" />
</a>

<br><br>

[![Jenkins](https://img.shields.io/badge/Jenkins-CI/CD-D24939?style=for-the-badge&logo=jenkins&logoColor=white)](https://www.jenkins.io/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestrated-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.0-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)

<br><br>

**A production-grade, fully automated CI/CD pipeline running entirely on your local machine.** <br>
*Push code ➔ Jenkins builds & tests ➔ Docker containerizes ➔ Kubernetes deploys.*

</div>

---

## 🛠️ Technology Stack

<div align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=py,flask,bootstrap,js,docker,kubernetes,jenkins,git,github,linux,nginx&perline=11" alt="Tech Stack" />
  </a>
</div>

---

## ✨ Enterprise Features

<details>
<summary><b>🔐 Secure Authentication & Roles</b> (Click to expand)</summary>
<br>
<ul>
  <li>Complete Login, Signup, and Logout flows using <code>Flask-Login</code>.</li>
  <li>Passwords securely hashed using <code>Werkzeug</code> security.</li>
  <li>Role-Based Access Control (RBAC): Admin vs. Standard User panels.</li>
</ul>
</details>

<details>
<summary><b>📊 Interactive & Dynamic Dashboard</b> (Click to expand)</summary>
<br>
<ul>
  <li>Real-time, animated charts powered by <code>Chart.js</code>.</li>
  <li>Responsive UI built with <code>Bootstrap 5</code>.</li>
  <li>Beautiful hover effects and custom CSS transitions.</li>
</ul>
</details>

<details>
<summary><b>🚀 Automated CI/CD Pipeline</b> (Click to expand)</summary>
<br>
<ul>
  <li>Jenkins pipelines as code (<code>Jenkinsfile</code>).</li>
  <li>Automatic trigger on Git push (SCM Polling).</li>
  <li>Built-in smoke testing using <code>curl</code> before deployment.</li>
  <li>Docker image tagging using the Jenkins <code>BUILD_NUMBER</code>.</li>
</ul>
</details>

<details>
<summary><b>☸️ Kubernetes Orchestration</b> (Click to expand)</summary>
<br>
<ul>
  <li>Declarative Kubernetes manifests (<code>deployment.yaml</code>, <code>service.yaml</code>).</li>
  <li>Self-healing: Auto-restarts failed pods.</li>
  <li>High Availability: Runs 2 replicas by default.</li>
  <li>Zero-downtime rolling updates.</li>
</ul>
</details>

---

## 🏗️ System Architecture

```mermaid
graph TD
    A["👨‍💻 Developer Push"] -->|git push| B("🐙 GitHub Repository")
    B -->|Poll SCM every 60s| C{"🤖 Jenkins Pipeline"}
    C -->|1. Checkout Code| D["🐳 Docker Build"]
    D -->|2. Build Image| E["🧪 Smoke Test"]
    E -->|3. curl /login| F{"Pass?"}
    F -->|Yes| G["☸️ Kubernetes Deploy"]
    F -->|No| H["❌ Build Fails & Alerts"]
    G -->|Rolling Update| I(("🚀 App Live on Port 30080"))
    
    style A fill:#0d6efd,color:#fff
    style B fill:#24292e,color:#fff
    style C fill:#d24939,color:#fff
    style G fill:#326ce5,color:#fff
    style I fill:#198754,color:#fff
```

---

## 🚦 Quick Start Guide

### 1️⃣ Prerequisites
Ensure you have the following installed:
*   [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Enable Kubernetes in settings)
*   [Git](https://git-scm.com/)
*   [Kubectl](https://kubernetes.io/docs/tasks/tools/)

### 2️⃣ Boot the Jenkins Server

```bash
cd jenkins-setup
docker compose up -d --build
```
> Access Jenkins at **`http://localhost:8080`** *(Get initial password via `docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword`)*

### 3️⃣ Configure the Pipeline
1. Create a new **Pipeline** job in Jenkins.
2. Point it to your GitHub repository.
3. Set the script path to `Jenkinsfile`.
4. Add a **Secret File** credential named `kubeconfig` (upload your local `~/.kube/config` file).

### 4️⃣ Deploy & Access
Push any change to GitHub. Jenkins will automatically build and deploy.

```bash
# Watch the pods spin up!
kubectl get pods -w
```

🎉 **Access the live application at:** `http://localhost:30080`

**Default Admin Credentials:**
*   **Username:** `admin`
*   **Password:** `admin123`

---

## 📸 Application Previews

| 🔐 Login Page | 📊 Interactive Dashboard |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x250/0d6efd/ffffff?text=Beautiful+Login+Screen" alt="Login"> | <img src="https://via.placeholder.com/400x250/198754/ffffff?text=Interactive+Charts" alt="Dashboard"> |

| 🛡️ Admin Panel | 📝 Sign Up Page |
| :---: | :---: |
| <img src="https://via.placeholder.com/400x250/dc3545/ffffff?text=User+Management" alt="Admin"> | <img src="https://via.placeholder.com/400x250/ffc107/ffffff?text=Secure+Sign+Up" alt="Signup"> |

---

## 📂 Project Structure

```text
flask-cicd-app/
├── 📁 jenkins-setup/        # Custom Jenkins Docker setup
├── 📁 k8s/                  # Kubernetes Manifests
│   ├── deployment.yaml      # Pod definitions
│   └── service.yaml         # NodePort service
├── 📁 static/               # CSS & JavaScript files
├── 📁 templates/            # HTML templates
├── 🐍 app.py                # Main Flask Application
├── 🐳 Dockerfile            # App Container
├── 🐳 docker-compose.yml    # Local runtime setup
├── ⚙️ Jenkinsfile           # CI/CD Pipeline
├── 📄 requirements.txt      # Python dependencies
└── 📖 README.md             # You are here!
```

---

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:326ce5,100:0d6efd&height=120&section=footer" width="100%" />
```
