pipeline {
  agent any
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('checkout') {
      steps {
        checkout scm
      }
    }
    stage('Test1') {
      steps {
        sh '''
          java -version
        '''
      }
    }
  }
}
