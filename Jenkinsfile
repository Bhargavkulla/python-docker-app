pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'bhargavakulla/python-app:latest'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/Bhargavkulla/python-docker-app.git',branch:'main'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }
        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
        
    }
}
