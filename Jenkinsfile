pipeline {
    agent any
    stages {
        stage('Cleanup Old Container') {
            steps {
                powershell 'if (docker ps -a -q -f "name=my-web-server") { docker stop my-web-server; docker rm my-web-server }'
            }
        }
        stage('Build Image') {
            steps {
                powershell 'docker build -t my-nginx-web .'
            }
        }
        stage('Deploy') {
            steps {
                powershell 'docker run -d --name my-web-server -p 8081:80 my-nginx-web'
            }
        }
    }
}
