pipeline {
    agent any
    stages {
        stage('develop Branch Deploy Code') {
            when {
                branch 'develop'
            }
            steps {
                sh """
                  sh "aws eks --region ap-south-1 update-kubeconfig --region ${ap-south-1} --name ${elysium-uit-eks}"
                  cd Demo/k8s.yaml  kubectl apply -f k8s.yaml
                """
 
                sh """
                echo "Deploying Code from develop branch"
                """
            }
        }
      stage('Docker Build') {
    	agent any
      steps {
      	sh 'cd Demo/Dockerfile  docker build -t naveen0515/node:latest .'
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



