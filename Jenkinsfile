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
        //sh 'go mod init example/hello'
        sh 'go build'
      }
    }

    stage('Test') {
      steps {
        sh 'go test ./... -coverprofile=coverage.txt'
        sh "curl -s https://codecov.io/bash | bash -s -"        
      }
    }

    stage('Code Analysis') {
      steps {
        sh 'curl -sfL https://install.goreleaser.com/github.com/golangci/golangci-lint.sh | bash -s -- -b $GOPATH/bin v1.18.0'
        sh 'golangci-lint run'
      }
    }
  }
}
