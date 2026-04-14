pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh '''
                docker run --rm -v $PWD:/app -w /app node:18 npm install
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sample-api .'
            }
        }

        stage('Deploy Container') {
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