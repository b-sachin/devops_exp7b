pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/b-sachin/devops_exp7b.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-cicd-app:latest .'
            }
        }

        stage('Load Image to Minikube') {
            steps {
                bat 'minikube image load flask-cicd-app:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }
}