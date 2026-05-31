pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo "Code already checked out by Jenkins"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t poc-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop poc || true
                docker rm poc || true
                docker run -d -p 5000:5000 --name poc poc-app
                '''
            }
        }
    }
}
