pipeline {
    agent any

    environment {
        IMAGE_NAME     = "flask-cicd-app"
        CONTAINER_NAME = "flask-cicd-app"
        APP_PORT       = "5000"
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📦 Code checked out from Git'
                sh 'ls -la'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo '🐳 Building Docker image...'
                sh "docker build -t ${IMAGE_NAME}:${BUILD_NUMBER} -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Test Image') {
            steps {
                echo '🧪 Quick smoke test...'
                sh """
                    docker run -d --name test-${CONTAINER_NAME}-${BUILD_NUMBER} -p 5055:5000 ${IMAGE_NAME}:${BUILD_NUMBER}
                    sleep 5
                    curl -f http://localhost:5055/login || (docker logs test-${CONTAINER_NAME}-${BUILD_NUMBER} && exit 1)
                    docker stop test-${CONTAINER_NAME}-${BUILD_NUMBER}
                    docker rm test-${CONTAINER_NAME}-${BUILD_NUMBER}
                """
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying new version...'
                sh """
                    docker stop ${CONTAINER_NAME} || true
                    docker rm ${CONTAINER_NAME} || true
                    docker run -d --name ${CONTAINER_NAME} -p ${APP_PORT}:5000 ${IMAGE_NAME}:${BUILD_NUMBER}
                """
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline succeeded. App live at http://localhost:${APP_PORT}"
        }
        failure {
            echo "❌ Pipeline failed. Check logs above."
        }
    }
}