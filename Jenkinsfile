pipeline {

  agent {
    label 'SLAVE'
  }

  environement {
    NEXUS=credentials('Nexus')
  }
  stages {

    stage('Install Npm Dependencies') {
      steps {
        sh '''
          npm install
        '''
      }
    }

    stage('Create Archive to Upload') {
      steps {
        sh '''
          tar -czf user-service-${BUILD_NUMBER}.tgz node_modules package.json  server.js
        '''
      }
    }

    stage('Upload To Nexus') {
      steps {
        sh '''
          curl -v -u $NEXUS --upload-file user-service-${BUILD_NUMBER}.tgz https://nexus.devopsb46.online/repository/user-service/user-service-${BUILD_NUMBER}.tgz
        '''
      }
    }

  }
}