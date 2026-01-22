pipeline {
    agent any
    stages {
        stage('Cleanup') {
            steps {
                // We use 'sh' now because Jenkins is in a Linux container
                sh 'docker stop my-web-server || true'
                sh 'docker rm my-web-server || true'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t my-custom-nginx .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d --name my-web-server -p 8090:80 my-custom-nginx'
            }
        }
    }
}