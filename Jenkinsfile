pipeline {
  agent {
    kubernetes {
      label 'app'  // all your pods will be named with this prefix, followed by a unique id
      idleMinutes 2  // how long the pod will live after no jobs have run on it
    }
  }
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
