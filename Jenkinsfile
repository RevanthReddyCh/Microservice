pipeline {
    agent any

    stages {
        stage('Pull,Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/adservice:latest"
                        sh "docker tag adijaiswal/adservice:latest revanthreddych/adservice:latest"
                        sh "docker build -t revanthreddych/adservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker IMAGE') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/adservice:latest "
                    }
                }
            }
        }
    }
}
