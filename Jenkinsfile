pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://B14003C910FBF1A014030F65DE7AF61F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapp', serverUrl: 'https://B14003C910FBF1A014030F65DE7AF61F.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapp"
                }
            }
        }
    }
}
