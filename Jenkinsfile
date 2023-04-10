pipeline {
    agent {
        kubernetes {
            label 'my-pod'
            containerTemplate {
                name 'docker'
                image 'docker:latest'
                ttyEnabled true
                command 'cat'
            }
        }
    }
    stages {
        stage('Docker Build') {
            steps {
                dir('docker') {
                    sh 'docker build -t naveen0515/myimage:latest .'
                }
            }
        }
        stage('Docker Push') {
            steps {
                sh 'docker login -
                sh 'docker 
            }
        }
    }
}
