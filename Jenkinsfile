pipeline {
    agent any
    stages {  
       stage('Build') {
           steps {
               withCredentials([[
               $class: 'AmazonWebServicesCredentialsBinding',
               accessKeyVariable: 'AKIAWGOPPSWTFLOWGIEP',
               secretKeyVariable: '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',
               credentialsId: 'kubeconfigfile']])
          }           
      }
      stage('Deploy to Kubernetes') {
          steps {
              kubernetesDeploy(
              kubeconfigId: '',
              configFilePath: '/home/ubuntu/.kube',
              namespace: 'my-namespace',
              yamlPath: '/home/ubuntu/k8s.yaml',)
          }       
      }
      stage('main Branch Deploy Code') {
            steps {
                withCredentials([file(credentialsId: 'elysium-uit-eks', Kubeconfigfile:'/home/ubuntu/.kubeconfig')]) {
                   sh 'mkdir -p ~/.kube'
                   sh 'cat $AWS_UIT_KUBECONFIG> ~/.kube/config'
                   sh 'aws eks --region ap-south-1 update-kubeconfig --region ${ap-south-1} --name ${elysium-uit-eks}'
                   sh 'kubectl apply -f k8s.yaml'
                   sh  'echo "Deploying Code from main branch'
            }
     }
     stage('Docker Build') {
         steps {
        	sh 'Dockerfile  docker build -t naveen0515/node:latest',
         }
    }
    stage('Docker Push') {
        steps {
      	   withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
           sh 'docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}'
           sh 'docker push Naveen0515/node:latest'
        
       }
   } 
  }
  }         
