pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/mangalgirase/sample-node-api.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-api .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop sample-api || true
                docker rm sample-api || true
                docker run -d -p 3000:3000 --name sample-api sample-api
                '''
            }
        }
    }
}