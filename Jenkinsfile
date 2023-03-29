pipeline {
  agent {
    docker {
      image 'node:14'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        sh 'npm run build'
        sh 'docker build -t my-app .'
        sh 'docker tag my-app:latest my-registry/my-app:latest'
        sh 'docker push my-registry/my-app:latest'
      }
    }
    stage('Deploy') {
      steps {
        sh 'kubectl apply -f k8s.yaml'
      }
    }
  }
}





