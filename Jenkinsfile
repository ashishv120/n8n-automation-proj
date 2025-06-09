pipeline {
    agent any

    environment {
        COMPOSE_FILE = 'docker-compose.yml'
        PROJECT_DIR = "${env.WORKSPACE}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Cloning repo..."
            }
        }

        stage('Stop Old Container') {
            steps {
                script {
                    sh "docker-compose down || true"
                }
            }
        }

        stage('Deploy n8n') {
            steps {
                script {
                    sh "docker-compose up -d"
                }
            }
        }
    }

    post {
        success {
            echo "n8n Deployed Successfully!"
        }
        failure {
            echo "Deployment Failed"
        }
    }
}
