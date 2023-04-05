pipeline {
    agent any
    environment {
        KUBECONFIG = '/home/ubuntu/.kubeconfig'
    }
    stages {  
        stage('Build') {
            steps {
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    accessKeyVariable: 'AKIAWGOPPSWTFLOWGIEP',
                    secretKeyVariable: '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',
                    credentialsId: 'kubeconfigfile'
                ]])
            }           
        }
        stage('Deploy to Kubernetes') {
            steps {
                kubernetesDeploy(
                    kubeconfigId: '',
                    configFilePath: '/home/ubuntu/.kube',
                    namespace: 'my-namespace',
                    yamlPath: '/home/ubuntu/k8s.yaml'
                )
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t naveen0515/node:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker push naveen0515/node:latest'
                }
            }
        }
        stage('main Branch Deploy Code') {
            steps {
                withCredentials([file(credentialsId: 'elysium-uit-eks', variable: 'Kubeconfigfile')]) {
                    sh 'mkdir -p ~/.kube'
                    sh 'cat $Kubeconfigfile > ~/.kube/config'
                    sh "aws eks --region ap-south-1 update-kubeconfig --name elysium-uit-eks"
                    sh 'kubectl apply -f k8s.yaml'
                    sh 'echo "Deploying Code from main branch"'
                }
            }
        }
    }
}
