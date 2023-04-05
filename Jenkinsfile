pipeline {
  agent any
  stages {  
    stage('Build') {
      steps {
        withCredentials([
          [ $class: 'AmazonWebServicesCredentialsBinding',
            accessKeyVariable: 'AKIAWGOPPSWTFLOWGIEP',
            secretKeyVariable: '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',
            credentialsId: 'kubeconfigfile']
        ]) {
          // do build steps
        }
      }
    }
    stage('Deploy to Kubernetes') {
      steps {
        kubernetesDeploy(
          kubeconfigId: 'kubeconfigfile',
          configFilePath: '/home/ubuntu/.kube',
          namespace: 'my-namespace',
          yamlPath: '/home/ubuntu/k8s.yaml'
        )
      }       
    }
    stage('main Branch Deploy Code') {
      steps {
        withCredentials([file(credentialsId: 'elysium-uit-eks', variable: 'Kubeconfigfile')]) {
          sh 'mkdir -p ~/.kube'
          sh 'cat $Kubeconfigfile> ~/.kube/config'
          sh 'aws eks --region ap-south-1 update-kubeconfig --region ap-south-1 --name elysium-uit-eks'
          sh 'kubectl apply -f k8s.yaml'
          sh 'echo "Deploying Code from main branch"'
        }
      }       
    } 
  } 
}
