pipeline { 
    agent any

    stages {
        stage('Deploy To kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kube-id', namespace: 'ekart', serverUrl: 'https://C1EDDE1CC894DACD26D0E035EB85E93D.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        stage('verify') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'kube-id', namespace: 'ekart', serverUrl: 'https://C1EDDE1CC894DACD26D0E035EB85E93D.yl4.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n ekart"
                }
            }
        }
    }
}
