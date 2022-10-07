pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
        credentialsId: 'renomas1',
        url: 'https://github.com/renomas1/pvweb'
            }
        }
    stage('delete container') {
      steps {
        sh '''
        sudo kubectl delete pod web
        '''
      }
    }
    stage('create container') {
      steps {
        sh '''
        sudo cat index.html
                '''
      }
    }
    stage('copy') {
      steps {
        sh '''
        sudo kubectl run web --image=httpd --port 80
        '''
      }
    }
  }
}
