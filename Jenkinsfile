pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/YOUR_USERNAME/flask-cicd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-cicd-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-cicd flask-cicd-app'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            sh 'docker stop flask-cicd || true'
            sh 'docker rm flask-cicd || true'
        }
    }
}
