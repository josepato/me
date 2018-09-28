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
            mail(subject: 'test me jenkins', body: 'this is a test', to: 'josepato@linkaform.com')
            emailext(subject: 'extend mail', body: 'exeten mail', attachLog: true, to: 'test')
          }
        }
      }
    }
    stage('Wait') {
      steps {
        input(message: 'Approved', submitter: 'test')
      }
    }
    stage('Send Mail2') {
      steps {
        mail(subject: 'Deploy', body: 'boyd', to: 'josepato@linkaform.com')
        emailext(subject: 'Deply', body: 'deploy', attachLog: true, to: 'real')
      }
    }
    stage('deploya') {
      steps {
        input(message: 'deploy a', submitter: 'real')
      }
    }
  }
}