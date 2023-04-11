pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b790e065-bc9e-4994-b19b-977dd852686c', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
    
    stage('Build and Run Project') {
  steps {
    sh 'cd my-project'
    sh '/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin/npm install'
    sh '/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin/npm run serve'
  }
}
  }
}