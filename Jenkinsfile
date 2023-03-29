pipeline {
    agent any
    stages {
        stage('develop Branch Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                   kubectl apply -f k8s.yaml
                """
 
                sh """
                echo "Deploying Code from Main branch"
                """
            }
        }
        stage('main Branch Deploy Code') {
            when {
                branch 'main'
            }
            steps {
                sh """
                echo "Building Artifact from main branch"
                """
                sh """
                echo "Deploying Code from main branch"
                """
           }
        }
    }
}
