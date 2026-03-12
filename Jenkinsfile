pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/b-sachin/devops_exp7b.git'
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
                bat 'set KUBECONFIG=%USERPROFILE%\\.kube\\config && kubectl apply -f deployment.yaml'
                bat 'set KUBECONFIG=%USERPROFILE%\\.kube\\config && kubectl apply -f service.yaml'
            }
        }
    }
}