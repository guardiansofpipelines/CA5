pipeline {
    agent any
    stages {
        stage('Build and Publish Web Service Docker Image') {
            steps {
                sh 'docker build -t mywebservice:latest .'
                sh 'docker push mywebservice:latest'
            }
        }
    }
}
