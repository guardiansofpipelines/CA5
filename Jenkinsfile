pipeline {
    agent any
    stages {
        stage('Execute Docker Compose') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}