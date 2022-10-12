pipeline {
  agent any
  stages {
    stage('CheckGitHub') {
      steps {
        git branch: 'main',
        credentialsId: 'renomas1',
        url: 'https://github.com/renomas1/pvweb'
            }
        }
    stage('Delete Service') {
      steps {
        sh '''
        sudo kubectl delete hpa wordpress-autoscale
        sudo kubectl delete -k ./
	sudo kubectl delete -f pv1.yml
	sudo kubectl delete -f pv2.yml
        '''
      }
    }
    stage('Create Service') {
      steps {
        sh '''
	sudo kubectl apply -f pv1.yml
	sudo kubectl apply -f pv2.yml
        sudo kubectl apply -k ./
                '''
      }
    }
  }
}
