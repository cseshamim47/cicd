pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh "docker build -t myapp:${BUILD_NUMBER} ."
            }
        }

        stage('Run Container') {
            steps {
                sh "docker rm -f myapp || true"
                sh "docker run -d -p 5000:5000 --name myapp myapp:${BUILD_NUMBER}"
            }
        }
    }
}
