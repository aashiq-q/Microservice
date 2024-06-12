pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'minikube', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://192.168.39.126:8443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'minikube', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://192.168.39.126:8443']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
