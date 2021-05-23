pipeline {
    agent none
    environment {
        GOCACHE = '/tmp/.cache'
    }
    stages {
        stage('lint') {
            agent {
                docker {
                    image 'golangci/golangci-lint:v1.40-alpine'
                }
            }
            steps {
                sh 'golangci-lint run'
            }
        }
        stage('version') {
            agent {
                docker {
                    image 'golang:1.16.4-alpine3.13'
                }
            }
            steps {
                sh 'go version'
            }
        }
        stage('test') {
            agent {
                docker {
                    image 'golang:1.16.4-alpine3.13'
                }
            }
            steps {
                sh 'go test'
            }
        }
        stage('build') {
            agent {
                docker {
                    image 'golang:1.16.4-alpine3.13'
                }
            }
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
