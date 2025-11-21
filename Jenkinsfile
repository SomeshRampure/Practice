pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop', url: 'https://github.com/SomeshRampure/Practice.git'
            }
        }

        stage('Build') {
            steps {
                bat 'echo Building MyApp on Windows > build.log'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Running tests... > test.log'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: '*.log', fingerprint: true
            }
        }
    }

    post {
        success {
            mail to: 'your-email@example.com',
                 subject: "SUCCESS: Jenkins Build #${env.BUILD_NUMBER}",
                 body: "Build completed successfully. Artifacts archived."
        }
        failure {
            mail to: 'your-email@example.com',
                 subject: "FAILURE: Jenkins Build #${env.BUILD_NUMBER}",
                 body: "Build failed. Please check logs."
        }
    }
}
