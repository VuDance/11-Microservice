pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://AA0B242BD802CDFD1B608358805E1E69.gr7.ap-southeast-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl apply -f deployment-service.yml' // our main branch file
                } 
            }
        }

        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'EKS-1', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://AA0B242BD802CDFD1B608358805E1E69.gr7.ap-southeast-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl get svc -n webapps'
                } 
            }
        }
    }
}
