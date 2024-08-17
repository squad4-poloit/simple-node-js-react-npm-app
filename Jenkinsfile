pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "your-nodejs-backend-image"
        DOCKER_REGISTRY = "your-docker-registry" // Replace with your Docker registry if needed
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    sh 'npm start'
                }
            }
        }
    }
}
