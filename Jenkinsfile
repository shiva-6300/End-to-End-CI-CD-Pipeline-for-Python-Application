pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/shiva-6300/End-to-End-CI-CD-Pipeline-for-Python-Application.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-ecommerce-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-container flask-ecommerce-app'
            }
        }

    }
}
