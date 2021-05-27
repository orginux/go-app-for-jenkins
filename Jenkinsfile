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
        stage('Linters') {
            parallel {
                stage('golangci-lint') {
                    environment {
                        GOLANGCI_LINT_CACHE = '/tmp/.cache'
                    }
                    agent {
                        docker {
                            image 'golangci/golangci-lint:v1.40-alpine'
                        }
                    }
                    steps {
                        sh 'golangci-lint run'
                    }
                }
                stage('go-fmt') {
                    steps {
                        sh 'gofmt -e -d .'
                    }
                }
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
