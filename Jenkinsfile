pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b790e065-bc9e-4994-b19b-977dd852686c', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
    
    stage('Check NodeJS version') {
      steps {
        
          sh 'npm version'
      }
    }
    
    stage('Build') {
      steps {
        withEnv(['PATH+NODE=/usr/bin']) {
          sh 'npm run build'
        }
      }
    }
  }
}