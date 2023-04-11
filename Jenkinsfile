pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b790e065-bc9e-4994-b19b-977dd852686c', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
   
    stage('Install Dependencies') {
      steps {
        sh 'cd my-project && npm install'
      }
    }
    stage('Build and Run Project') {
      steps {
        
        sh 'export PATH=$PATH:/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin && npm run build'
      }
    }
  }
}