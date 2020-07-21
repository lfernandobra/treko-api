pipeline {
  agent {
    docker {
      image "node:8-alpine"
      args "--network=skynet"
    }
  }
  stages {
    stage("Build") {
      steps {
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/latest-stable/main' >> /etc/apk/repositories"
        sh "echo 'http://dl-cdn.alpinelinux.org/alpine/latest-stable/community/' >> /etc/apk/repositories"
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
