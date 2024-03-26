pipeline {
  agent any

  tools {
    go 'Go-1.22.1'
  }

  environment {
    GO111MODULES = 'on'
  }
  
  stages {
    stage('Build') {
      steps {
        sh 'go mod init'
        sh 'go build'
      }
    }
  }
}
