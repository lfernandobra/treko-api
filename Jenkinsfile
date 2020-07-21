pipeline {
  agent {
    docker {
      image "node:8-alpine"
    }
  }
  stages {
    stage("Build") {
      steps {
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.6/main' >> /etc/apk/repositories"
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/v3.6/community/' >> /etc/apk/repositories"
        sh "apk update"
        sh "apk add --no-cache mongodb"
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
