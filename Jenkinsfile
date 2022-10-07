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
        sudo kubectl delete -k ./
        '''
      }
    }
    stage('create container') {
      steps {
        sh '''
        sudo kubectl apply -k ./
                '''
      }
    }
    stage('copy') {
      steps {
        sh '''
        sudo kubectl get service
        '''
      }
    }
  }
}
