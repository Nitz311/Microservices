pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6B282A1885AEB58031EC0CABC1C27000.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6B282A1885AEB58031EC0CABC1C27000.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
