pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                         sh "docker pull adijaiswal/paymentservice:latest"
                        sh "docker tag adijaiswal/paymentservice:latest revanthreddych/paymentservice:latest"
                        sh "docker build -t revanthreddych/paymentservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/paymentservice:latest"
                        sh "docker rmi adijaiswal/paymentservice:latest"
                        sh "docker rmi revanthreddych/paymentservice:latest"
                    }
                }
            }
        }
    }
}
