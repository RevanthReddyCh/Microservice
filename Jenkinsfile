pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
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
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/cartservice:latest "
                    }
                }
            }
        }
    }
}
