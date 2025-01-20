pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BD77C4680BF2C61C541ED601F24E9AD5.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'my-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://BD77C4680BF2C61C541ED601F24E9AD5.sk1.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
