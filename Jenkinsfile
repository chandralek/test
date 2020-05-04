pipeline {
  
  agent {
    label 'SLAVE'
  }

  stages {

    stage('Install Npm Dependencies') {
      steps {
        sh '''
          npm install
        '''
      }
    }


  }
}