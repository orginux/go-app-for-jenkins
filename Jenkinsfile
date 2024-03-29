pipeline {
    agent none
    environment {
        GOCACHE = '/tmp/.cache'
    }
    stages {
        stage('golangci-lint') {
            agent {
                docker {
                    image 'golangci/golangci-lint:v1.41-alpine'
                }
            }
            environment {
                GOLANGCI_LINT_CACHE = '/tmp/.cache'
            }
            steps {
                sh 'golangci-lint run'
            }
        }
        stage("build and test the project"){
            agent {
                docker {
                    image 'golang:1.16.4-alpine3.14'
                }
            }
            stages{
                stage('version') {
                    steps {
                        sh 'go version'
                    }
                }
                stage('go-fmt') {
                    steps {
                        sh 'gofmt -e -d .'
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
    }
}
