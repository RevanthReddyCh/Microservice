pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/productcatalogservice:latest"
                        sh "docker tag adijaiswal/productcatalogservice:latest revanthreddych/productcatalogservice:latest"
                        sh "docker build -t revanthreddych/productcatalogservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/productcatalogservice:latest"
                        sh "docker rmi adijaiswal/productcatalogservice:latest"
                        sh "docker rmi revanthreddych/productcatalogservice:latest"
                    }
                }
            }
        }
    }
}
