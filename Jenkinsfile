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
        stage('Docker') {
            when {
                branch 'main'
            }
            steps {
      	sh 'docker build -t shanem/spring-petclinic:latest .'
      }
        }
    }
}



