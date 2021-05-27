pipeline {
    agent {
        docker {
            image 'golang:1.16.4-alpine3.13'
        }
    }
    environment {
        GOCACHE = '/tmp/.cache'
    }
    stages {
        stage('go-fmt') {
             steps {
                sh 'gofmt -e -d .'
            }
        }
        stage('version') {
            steps {
                sh 'go version'
            }
        }
        stage('test') {
            steps {
                sh 'go test'
            }
        }
        stage('build') {
            environment {
                GO111MODULE = 'on'
                CGO_ENABLED = 0
                GOOS        = 'linux'
            }
            steps {
                sh 'go build -o hello-world'
            }
        }
    }
}
