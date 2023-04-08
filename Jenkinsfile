pipeline {
    agent {
        kubernetes {
            // Pod template specification
            yaml """
                apiVersion: v1
                kind: Pod
                metadata:
                  labels:
                    app: my-app
                spec:
                  containers:
                  - name: maven
                    image: maven:3.8.1-jdk-11
                    command: ["cat"]
                    tty: true
            """
        }
    }
    stages {  
        stage('Build') {
            st
                ]])
            }           
        }
        stage('Deploy to Kubernetes') {
            steps {
                kubernetesDeploy(
                    kubeconfigId: 'kube-configdemo',
                    configFilePath: '/home/ubuntu/.kubeconfig',
                    namespace: 'eks-sample-app',
                    yamlPath: '/home/ubuntu/k8s.yaml'
                )
            }
        }
        stage('Docker Build') {
            steps {
                dir('docker.Dockerfile')
                sh 'docker build -t naveen0515/myimage:latest .'
            }
        }
        stage('Docker Push') {
            steps {
                withCredentials([usernamePassword(credentialsId', passwordVariable: , usernameVariable: 'Naveen@515')]) {
                    sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
                    sh 'docker push naveen0515/node:latest'
                }
            }
        }
        stage('main Branch Deploy Code') {
            steps {
          
                }
            }
        }
    }
}
