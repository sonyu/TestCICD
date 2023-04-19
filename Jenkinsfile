pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'd26f4a7f043841e9a803813b116bd84b', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
   
    stage('Install Dependencies') {
      steps {
        sh 'cd /var/jenkins_home/workspace/test_cicd/my-project && npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'export PATH=$PATH:/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin:/usr/local/lib/node_modules/@vue/cli/bin && cd /var/jenkins_home/workspace/TestCICDPipeline/my-project && npm install --save-dev @vue/cli-service && npm run build'
      }
    }  
    stage('Get Latest Commit') {
      steps {
        sh 'git log -n 1 --pretty=format:"%h - %an, %ar : %s"'
      }
    }  
  }
}