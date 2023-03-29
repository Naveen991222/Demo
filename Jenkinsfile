pipeline {
    agent any
    stages {
        stage('Main Branch Deploy Code') {
            when {
                branch 'main'
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
        stage('Develop Branch Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                echo "Building Artifact from Develop branch"
                """
                sh """
                echo "Deploying Code from Develop branch"
                """
           }
        }
    }
}
