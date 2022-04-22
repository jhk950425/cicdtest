pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/jhk950425/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t jhk950425/testweb:newnewshop .
        sudo docker push jhk950425/testweb:newnewshop
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth
	sudo kubectl set image deployment deploy-shop ctn-shop=jhk950425/testweb:newnewshop
        '''
      }
    }
  }
}
