pipeline {
    agent any
    tools {
        go 'go-1.16'
    }
    stages {
        stage('test') {
            steps {
                go test
            }
        }
        stage('build') {
            environment {
                GO111MODULE = 'on'
                CGO_ENABLED = 0
                GOOS        = 'linux'
            }
            steps {
                sh 'go build -o webserver'
            }
        }
    }
}
