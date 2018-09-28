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
      parallel {
        stage('Wait') {
          steps {
            input(message: 'Approved', submitter: 'test')
            input(message: 'Aprovee', submitterParameter: 'devel')
            input(message: 'aporve2', submitterParameter: 'real')
          }
        }
        stage('subwait') {
          steps {
            input(message: 'admin', submitter: 'admin')
          }
        }
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