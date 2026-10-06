pipeline {
    agent any

    stages {
        stage('Cleanup Old Container & Image') {
            steps {
                echo 'Cleaning up existing container and image...'
                sh 'docker rm -f container_1 || true'
                sh 'docker rmi ubuntu:latest || true'
            }
        }

        stage('Pull Docker Image') {
            steps {
                echo 'Pulling ubuntu:latest Docker image...'
                sh 'docker pull ubuntu:latest'
            }
        }

        stage('Create & Run Container') {
            steps {
                echo 'Creating new container...'
                sh 'docker run -d --name container_1 -p 9090:80 ubuntu:latest'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline has failed.'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}