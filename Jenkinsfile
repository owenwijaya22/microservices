pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/owenwijaya22/microservices.git', branch: 'master')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build Docker') {
      steps {
        sh 'docker compose build'
      }
    }

  }
}