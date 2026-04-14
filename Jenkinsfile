pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {
        stage('Check Node') {
            steps {
                sh 'node -v && npm -v'
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

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 3000:3000 sample-api'
            }
        }
    }
}