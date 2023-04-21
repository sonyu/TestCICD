pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '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', url: 'https://github.com/sonyu/TestCICD.git']]])
      }
    }
   
    stage('Install Dependencies') {
      steps {
        sh 'cd /var/jenkins_home/workspace/test_cicd/my-project && npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'export PATH=$PATH:/var/jenkins_home/tools/jenkins.plugins.nodejs.tools.NodeJSInstallation/node/bin:/usr/local/lib/node_modules/@vue/cli/bin && cd /var/jenkins_home/workspace/TestPipeline/my-project && npm install --save-dev @vue/cli-service && npm run build'
      }
    }  
    stage('Get Latest Commit') {
      steps {
        sh 'git log -n 1 --pretty=format:"%h - %an, %ar : %s"'
      }
    } 
    stage('Delivery') {
      steps {
        sh 'npm install -g firebase-tools'
        sh 'firebase login --no-localhost --ci'
        sh 'firebase deploy --token="MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCyS8cSgOhwpJp7\nmjXgLCzchSZOTBrxSkXsCxnnc+ABpCoA4nBxtQh30DGRuELzRCfqtsGNKySOirbw\n/FrnwIv2VUSso6vA9uMDWGwyuMdhCJPaHwpGOglVsq0FlE96CBmxArswmoQ0DZav\nyu4BxFfrW7HyzvQ+2ek6zv3KbuVwdZx+dT9flA2z6YbbdV2gArHTOS9DSz70w8iv\nwelawGDAtztm3EtWV5UKQycij/7LoISUlfRP0KMVXu2MM1VEtsUu6vW7fwtrcpRi\nxLQOauxBjAsmwJBnGqWmX2Ej5XfNZIvh03rOwe47Hm7sX92lBgGx44xUQLZ7G5jR\n/QDTfM57AgMBAAECggEABKL8D+otciFQqXexSpAUy9iTcAYJLBIOFfnlMWcsPltQ\nkByxuByMKnWzD0ERQN0GQILF3myXAkKXwabrB4ulYkFqrf4IRpLNfgG6I6cegllH\nfjN83n4ITjgEQpwltjsHENrafGmeLDU2QhZlBN6ItHjR4aicjkqBthxv7jkiLAn0\nW47Dd/1BVTI2an909/GNcKAqMOGvGSa1T+ETjGH7YeAJvPnfPkFNAZ14alWbD1OZ\nS2hIDriP7Lrdwdf+dnTu1rF5DbSdgwnwBU6VHjYmRqMlxufJW7JA0oIcrgJZFIhC\nZQlOvJd7IXNi6eNqqiui35HEHw86oK9xp3dWrXWiIQKBgQD3MTroOVZSuN+owP1P\nPiqaggmUhpa2gE+GbQMbI5Tf/+g6Ml+iLZpO/wUPotygId7Elx38JAQDwi0VTc0N\nQ3DqXoO7WZB3rLOncNI3WchqBYIdOzR3TX41qKGMW+4tujH1HZ7LQP1zaEpar+k1\n2ZZWvgWSkLw7lTHCaTuSAXqk6QKBgQC4phvD8bfU9DaPnsvvm9Mj0BlYlXLnTsHu\n5QVo4iTx53WWP2hnvqSn33Psrf4rP0egGxVjOId2OihI5yimgR5ad495XxqiV+m9\nzHqS8YX1nheHL7pKYeEjdgUKYP20BT2YvOoC/TRCdXLVIbl4Q8svRRKQGYB2rG3D\nWK8+gf0JwwKBgFYWZxWJIm8cw4fZ7l4yoFO/BeccGFDmzstaG8LP2YFJdm8OLBAn\nIZ5xYinX5k4+fX6pwl+Vi3Bjp5/LwKXl3uVAlVAiGRYUp1yhBhUQx6Nk17Omctc5\nvcKiP+DKA2EZf1yGPE89CweuQnbi3K1MYfdDpl0s2uFFTFcQnxZyPWxBAoGBAKTW\nHMlCWtKvpJl3sCTZ3ZYF6uqKl8XoJ/Zk2vxzjXmqH+2d801SAlmegDVUaicfWYiT\nRPeLelpPtrDGMyLY90jZnOpDvVoZ0x9NkErnc6f9lpFnSQ2n7T0j2YIXbcSsPP3B\n/8HlWibOBFJBxfmXw6YSKm0bZvQKH/6Yh/DsSADTAoGBAMM7so4CW2UAeACwPKGP\nfMZ6bOG48qKwjSoS4HnnrtmVnOdwEgBXa3eBHjEWgr27eHA8s0u4Jq0qm1H23uD9\nXYG3F3VmKf4o2tXQMXsCO4NKVLyFYmBUfe/nhg4Ubqd/ja1qaEO0tInzlDTk1sj6\nsW5j9Pz9MhHjXu9MuHukumXa"'
      }
    } 
  }
}