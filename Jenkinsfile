pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/yourusername/MyApp.git'
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