pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-6', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6EC5488AA01A3E2B0FFC37D5BDEE49A2.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-6', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6EC5488AA01A3E2B0FFC37D5BDEE49A2.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
