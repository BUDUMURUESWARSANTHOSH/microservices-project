pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-my', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5D27DA414D700BDB2B970C417AB7DFD4.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-my', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5D27DA414D700BDB2B970C417AB7DFD4.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
