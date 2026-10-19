cat > README.md << 'EOF'
# Flask CI/CD Demo App

A small Flask app with login, signup, dashboard (with charts),
and admin panel — built to demo a **fully local Jenkins + Docker pipeline**.

## Stack
- Flask + Flask-Login
- SQLite
- Chart.js + Bootstrap 5
- Docker + Jenkins

## Run locally
    pip install -r requirements.txt
    python app.py

Open http://localhost:5000
Default admin: **admin / admin123**

## CI/CD
See `Jenkinsfile` and `jenkins-setup/docker-compose.yml`.
EOF