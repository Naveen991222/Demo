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
      stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker build -t naveen0515/node:latest .'
      }
    }
    stage('Docker Push') {
    	agent any
      steps {
      	withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push Naveen0515/node:latest'
        }
      }
    }
}



