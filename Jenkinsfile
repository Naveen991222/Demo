pipeline {
    agent any
    environment {
       KUBECONFIG = '/home/ubuntu/.kubeconfig'
  }
  stages {
    stage('Deploy to Kubernetes') {
      steps {
        kubernetesDeploy(
          kubeconfigId: '',
          configFilePath: env.KUBECONFIG,
          namespace: 'my-namespace',
          yamlPath: '/home/ubuntu/k8s.yaml'
    stages {
        stage('main Branch Deploy Code')
            steps {
                 withCredentials([file(credentialsId: 'elysium-uit-eks', Kubeconfigfile:'/home/ubuntu/.kubeconfig')]) {
                   sh 'mkdir -p ~/.kube'
                   sh 'cat $AWS_UIT_KUBECONFIG> ~/.kube/config'
                 }
                sh """
                  sh "aws eks --region ap-south-1 update-kubeconfig --region ${ap-south-1} --name ${elysium-uit-eks}"
                   k8s.yaml  kubectl apply -f k8s.yaml
                """
 
                sh """
                echo "Deploying Code from main branch"
                """
            }
        }
      stage('Docker Build') {
    	agent any
      steps {
      	sh 'Dockerfile  docker build -t naveen0515/node:latest .'
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



