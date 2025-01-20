pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/frontend:latest"
                        sh "docker tag adijaiswal/frontend:latest revanthreddych/frontend:latest"
                        sh "docker build -t revanthreddych/frontend:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image and remove from local') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/frontend:latest"
                        sh "docker rmi adijaiswal/frontend:latest"
                        sh "docker rmi revanthreddych/frontend:latest"
                    }
                }
            }
        }
    }
}
