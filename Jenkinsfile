pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build and Test') {
            steps {
                sh 'docker inspect -f . node:6-alpine'
                sh 'docker build -t my-react-app .'
                sh 'docker run -p 3000:3000 my-react-app'
            }
        }
        stage('Deliver') {
            steps {
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh 'docker stop $(docker ps -q)'
            }
        }
    }
}
