pipeline {
    agent any

    environment {
        ARGOCD_SERVER = "https://43.204.219.50:30289/" // Replace with your ArgoCD server URL
        ARGOCD_TOKEN = credentials('argocd_token') // Use Jenkins credentials to securely store the ArgoCD API token
        APPLICATION_NAME = "$BUILD_NAME" // Replace with the name of your ArgoCD application
    }

    stages {
        stage('Deploy to Kubernetes via ArgoCD') {
            steps {
                script {
                    // Log in to ArgoCD using the API token
                    sh "argocd login --insecure --grpc-web --username argocduser --password $ARGOCD_TOKEN $ARGOCD_SERVER"

                    // Trigger a sync for the specified application
                    sh "argocd app sync $APPLICATION_NAME"
                }
            }
        }
    }
}



