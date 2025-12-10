pipeline {
    agent any
    
    environment {
        PATH = "${WORKSPACE}/go/bin:${PATH}"
    }

    stages {
        stage('Setup Go') {
            steps {
                echo 'Downloading Go...'
                sh 'curl -OL https://go.dev/dl/go1.22.0.linux-amd64.tar.gz'
                echo 'Extracting Go...'
                sh 'tar -C . -xzf go1.22.0.linux-amd64.tar.gz'
                sh 'go version'
            }
        }

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
