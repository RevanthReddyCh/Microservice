pipeline {
    agent any

    stages {
        stage('Pull, Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                       sh "docker pull adijaiswal/loadgenerator:latest"
                        sh "docker tag adijaiswal/loadgenerator:latest revanthreddych/loadgenerator:latest"
                        sh "docker build -t revanthreddych/loadgenerator:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image & remove from local') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/loadgenerator:latest"
                        sh "docker rmi adijaiswal/loadgenerator:latest"
                        sh "docker rmi revanthreddych/loadgenerator:latest"
                    }
                }
            }
        }
    }
}
