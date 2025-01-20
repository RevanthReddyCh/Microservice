pipeline {
    agent any

    stages {
        stage('Pull, Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {

                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/cartservice:latest"
                        sh "docker tag adijaiswal/cartservice:latest revanthreddych/cartservice:latest"
                        sh "docker build -t revanthreddych/cartservice:latest ."
                    }
                        }
                }
            }
        }
        
        stage('Push Docker Image & remove from local') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/cartservice:latest "
                        sh "docker rmi adijaiswal/cartservice:latest"
                        sh "docker rmi revanthreddych/cartservice:latest"
                    }
                }
            }
        }
    }
}
