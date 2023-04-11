pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b790e065-bc9e-4994-b19b-977dd852686c', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
    stage('Clean and Install') {
      steps {
        sh 'npm cache clean --force'
        sh 'rm -rf node_modules'
        sh 'cd my-project && npm cache clean --force && rm -rf node_modules && cd ..'
      }
    }
    stage('Install Dependencies') {
      steps {
        sh 'cd my-project && npm install -g @vue/cli && npm install'
      }
    }
    stage('Build and Run Project') {
      steps {
        sh 'cd my-project && export PATH=$PATH:/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin && npm install -g @vue/cli && npm install && npm run build && nohup npm run serve &'
      }
    }
  }
}