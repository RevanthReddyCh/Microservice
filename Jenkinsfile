pipeline {
    agent any

    stages {
        stage('Pull, Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/currencyservice:latest"
                        sh "docker tag adijaiswal/currencyservice:latest revanthreddych/currencyservice:latest"
                        sh "docker build -t revanthreddych/currencyservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image & remove from local') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/currencyservice:latest "
                        sh "docker rmi adijaiswal/currencyservice:latest"
                        sh "docker rmi revanthreddych/currencyservice:latest"
                    }
                }
            }
        }
    }
}
