pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'b790e065-bc9e-4994-b19b-977dd852686c', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
    stage('Install NodeJS') {
      steps {
        sh '''
          curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
          sudo apt-get install -y nodejs
        '''
      }
    }
    stage('Check NodeJS version') {
      steps {
        withEnv(['PATH+NODE=/usr/bin']) {
          sh 'node -v'
        }
      }
    }
    stage('Install Dependencies') {
      steps {
        withEnv(['PATH+NODE=/usr/bin']) {
          sh 'npm install'
        }
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