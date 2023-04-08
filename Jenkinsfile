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
