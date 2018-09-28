pipeline {
  agent any
  stages {
    stage('Install Npm') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      parallel {
        stage('Test') {
          steps {
            sh 'npm test'
          }
        }
        stage('Send Email') {
          steps {
            mail(subject: 'test me jenkins', body: 'this is a test')
          }
        }
      }
    }
  }
}