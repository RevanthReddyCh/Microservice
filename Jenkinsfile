pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/recommendationservice:latest"
                        sh "docker tag adijaiswal/recommendationservice:latest revanthreddych/recommendationservice:latest"
                        sh "docker build -t revanthreddych/recommendationservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/recommendationservice:latest"
                         sh "docker rmi adijaiswal/recommendationservice:latest"
                        sh "docker rmi revanthreddych/recommendationservice:latest"
                    }
                }
            }
        }
    }
}
