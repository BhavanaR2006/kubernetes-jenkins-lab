pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s/deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl rollout status deployment/github-web --timeout=120s'
                bat 'kubectl get deployments'
                bat 'kubectl get pods'
            }
        }
    }
}
