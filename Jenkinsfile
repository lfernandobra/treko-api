pipeline {
  agent {
    docker {
      image "node:8-alpine"
    }
  }
  stages {
    stage("Build") {
      steps {
        sh "apk update"
        sh "apk add --no-cache mongodb=3.4.4-r0"
        sh "mongo --version"
        sh "chmod +x ./scripts/dropdb.sh"
        sh "npm install"       
      }
    }
    stage("Test") {
      steps {
        sh "npm run test:ci"
      }  
    }  
  }
}
