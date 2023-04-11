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
        sh 'cd /var/jenkins_home/workspace/TestCICDPipeline/my-project && npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'export PATH=$PATH:/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin:/usr/local/lib/node_modules/@vue/cli/bin && cd /var/jenkins_home/workspace/TestCICDPipeline/my-project && npm install --save-dev @vue/cli-service && npm run build'
      }
    }
    stage('Run Project') {
      steps {
        sh 'npm run serve'
      }
    }
  }
}