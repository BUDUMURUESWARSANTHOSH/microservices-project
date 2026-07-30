pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-my', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://88FDC90CA959AD39CB3378E313FB20E8.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-my', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://88FDC90CA959AD39CB3378E313FB20E8.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
