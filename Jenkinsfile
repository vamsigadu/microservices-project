pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-vamsi1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://06978AA273BFD764C3148F3B712B4061.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-vamsi1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://06978AA273BFD764C3148F3B712B4061.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
