pipeline {
  agent {
    kubernetes {
      inheritFrom 'app'
      yaml '''
      apiVersion: v1
      kind: Pod
      spec:
        containers:
        - name: git
          image: bitnami/git:2.40.1
          command:
          - cat
          tty: true
'''
    }
  }
  options {
    buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')
  }
  stages {
    stage('checkout') {
      steps {
        container('git') {
          checkout scm
        }
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
