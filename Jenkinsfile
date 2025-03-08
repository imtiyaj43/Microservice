pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t imtiyaj43/checkoutservice:latest ."
                    }
                }
            }
        }
    
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push imtiyaj43/checkoutservice:latest "
                    }
                }
            }
        }
    }
}
