pipeline {
    agent any
    stage('Docker Build') {
      steps {
      	sh 'Dockerfile  docker build -t naveen0515/node:latest',
      }
    }
    stage('Docker Push') {
      steps {
      	withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push Naveen0515/node:latest'
        
      }
    } 
  }
}  
