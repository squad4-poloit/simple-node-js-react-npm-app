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

        //stage('Run Unit Tests') {
            //steps {
               // script {
                 //   sh 'npm test'
                //}
            //}
        //}

        stage('Build Docker Image') {
            steps {
                script {
                    sh """
                    docker build -t ${DOCKER_IMAGE}:${env.BUILD_NUMBER} .
                    docker tag ${DOCKER_IMAGE}:${env.BUILD_NUMBER} ${DOCKER_IMAGE}:latest
                    """
                }
            }
        }

        stage('Docker Compose Up') {
            steps {
                script {
                    sh 'docker-compose up -d'
                }
            }
        }
    }

    //post {
        //always {
            //echo 'Cleaning up...'
            //sh 'docker-compose down'
            //cleanWs()
        //}
        //success {
            //echo 'Pipeline succeeded!'
        //}
        //failure {
            //echo 'Pipeline failed!'
        //}
    //}
}
