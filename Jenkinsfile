pipeline {
    agent kubernetesuit
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
                sh 'docker login -u Naveen515 -p Naveen@515'
                sh 'docker push naveen0515/myimage:latest'
            }
        }
    }
}
