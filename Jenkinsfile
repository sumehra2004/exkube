pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                script {
                    // Build and push Docker image
                    bat 'docker build -t ex:latest .'
                    bat 'docker tag ex:latest sumehra2004/ex:latest'
                    bat 'docker push sumehra2004/ex:latest'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running tests...'
                }
            }
        }
        stage('Deploy') {
            steps {
                script{
                    bat 'minikube delete'
                    bat 'minikube start'
                    bat 'minikube addons enable dashboard'
                    bat 'kubectl apply -f my-kube1-deployment.yaml'
                    bat 'kubectl apply -f my-kube1-service.yaml'
                    bat 'minikube dashboard'
                    
                    echo 'Deploying application...'
                }
            }
        }
    }
}
