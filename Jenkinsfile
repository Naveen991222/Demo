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
        sh 'docker build -t node .'
        sh 'docker tag node:latest my-registry/node:latest'
        sh 'docker push my-registry/node:latest'
      }
    }
    stage('Deploy') {
      steps {
        sh 'kubectl apply -f k8s.yaml'
      }
    }
  }
}





