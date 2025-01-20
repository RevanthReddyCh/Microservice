pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/checkoutservice:latest"
                        sh "docker tag adijaiswal/checkoutservice:latest revanthreddych/checkoutservice:latest"
                        sh "docker build -t revanthreddych/checkoutservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/checkoutservice:latest "
                    }
                }
            }
        }
    }
}
