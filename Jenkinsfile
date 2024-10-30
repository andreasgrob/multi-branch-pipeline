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
          checkout scmGit(
    branches: [[name: '*/main']],
    userRemoteConfigs: [[url: 'https://github.com/andreasgrob/multi-branch-pipeline']],
    gitTool: '/usr/bin/git')
        }
      }
    }
    stage('Test5') {
      steps {
        sh '''
          sh build.sh
        '''
      }
    }
  }
}
