pipeline {
    agent any

    environment {
        BACKEND_IMAGE = 'guardiansofpipelines/ca4-web:latest'
        FRONTEND_IMAGE = 'guardiansofpipelines/ca4-db:latest'
    }

    stages {
        stage('Check Docker Images Existence') {
            steps {
                script {
                    def backendImageExists = sh(script: "docker image inspect ${BACKEND_IMAGE} &> /dev/null", returnStatus: true)
                    def frontendImageExists = sh(script: "docker image inspect ${FRONTEND_IMAGE} &> /dev/null", returnStatus: true)

                    if (!backendImageExists) {
                        error("Backend Docker image does not exist: ${BACKEND_IMAGE}")
                    }
                    if (!frontendImageExists) {
                        error("Frontend Docker image does not exist: ${FRONTEND_IMAGE}")
                    }
                }
            }
        }

        stage('Build and Run Docker Compose') {
            steps {
                script {
                    // Ensure the docker-compose.yaml file is in the current workspace
                    sh 'cp E:/Study/7th Semester/MLOps/CA5/docker-compose.yml ./docker-compose.yml'
                }
                // Build and run the Docker Compose services
                sh 'docker-compose up -d'
            }
        }
    }

    post {
        success {
            echo "Success"
            // Add post-build steps here if needed
        }
        failure {
            echo "Failure"
            // Add failure-handling steps here if needed
        }
    }
}
