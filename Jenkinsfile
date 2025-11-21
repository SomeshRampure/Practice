pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SomeshRampure/Practice.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t practice-demo:latest .'
            }
        }
        stage('Run Container') {
            steps {
                bat 'docker run --rm practice-demo:latest'
            }
        }
    }
    post {
        success {
            bat 'echo Build and Docker run succeeded!'
        }
        failure {
            bat 'echo Build failed!'
        }
    }
}