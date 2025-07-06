pipeline {
    agent any 
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
        IMAGE_NAME = "dockerdrushya/devops-mini-project"
       }
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Drushya29/Devops-mini-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $IMAGE_NAME .'
                }
            }
        }
        stage('Run container') {
            steps {
                script { 
                    sh """
                    docker stop devops-container || true
                    docker rm devops-container || true
                    docker run -d --name devops-container -p 80:80 $IMAGE_NAME
                    """
                }
           } 
       }
    }
}
