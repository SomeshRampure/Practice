pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/SomeshRampure/Practice.git'
      }
    }
    stage('Build') {
      steps {
        bat 'echo Building MyApp on Windows'
      }
    }
    stage('Test') {
      steps {
        bat 'echo Running tests...'
      }
    }
  }
}

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop', url: 'https://github.com/<your-username>/jenkins-ci-demo.git'
            }
        }
        stage('Build') {
            steps {
                bat 'echo Compiling project... > build.log'
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