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
        kubectl get pod
        '''
      }
    }
    stage('create container') {
      steps {
        sh '''
        sudo kubectl apply -f pv1.yml
	sudo kubectl apply -f pv2.yml
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
