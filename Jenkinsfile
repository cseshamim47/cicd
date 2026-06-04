pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t simple-html:${BUILD_NUMBER} ."
            }
        }

        stage('Deploy Container') {
            steps {
                sh "docker rm -f simple-html || true"
                sh "docker run -d -p 8081:80 --name simple-html simple-html:${BUILD_NUMBER}"
            }
        }
    }

    post {
        success {
            echo "CI/CD Success!"
        }

        failure {
            echo "CI/CD Failed!"
        }
    }
}
