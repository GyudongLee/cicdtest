pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/GyudongLee/cicdtest.git', branch: 'master'
      }
    }
    stage('docker build and push') {
      steps {
        sh '''
        sudo docker build -t dd0717/gyudong:newnewmain .
        sudo docker push dd0717/gyudong:newnewmain
        '''
      }
    }
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kauth

        sudo kubectl set image deployment deploy-main ctn-main=dd0717/gyudong:newnewmain
        '''
      }
    }
  }
}
