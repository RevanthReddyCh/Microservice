pipeline { 
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker pull adijaiswal/shippingservice:latest"
                        sh "docker tag adijaiswal/shippingservice:latest revanthreddych/shippingservice:latest"
                        sh "docker build -t revanthreddych/shippingservice:latest ."
                    }
                }
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-creds', toolName: 'docker') {
                        sh "docker push revanthreddych/shippingservice:latest "
                        sh "docker rmi adijaiswal/shippingservice:latest"
                        sh "docker rmi revanthreddych/shippingservice:latest"
                    }
                }
            }
        }
    }
}
