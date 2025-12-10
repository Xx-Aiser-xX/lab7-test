pipeline {
    agent any
    tools {
        go 'go-1.22' 
    }
    environment {
        GOCACHE = "${WORKSPACE}/.cache"
        GOPATH = "${WORKSPACE}/go"
        PATH = "${GOPATH}/bin:${PATH}"
    }
    stages {
        stage('Unit Tests') {
            steps {
                sh 'go test -v -run="TestHandler|TestHandler2"'
            }
        }
        stage('Integration Test') {
            steps {
                sh 'go test -v -run="TestIntegration"'
            }
        }
    }
}
