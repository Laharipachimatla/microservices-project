pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Commerce', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://00C164D1592B1268D0A9ECE89BC40C33.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Commerce', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://00C164D1592B1268D0A9ECE89BC40C33.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
