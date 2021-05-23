pipeline {
    agent {
        docker { image 'golang:1.16.4-alpine3.13' }
    }
    stages {
        stage('test') {
            agent {
                docker { image 'golang:1.16.4-alpine3.13' }
            }
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
                sh 'go build -o hello-world'
            }
        }
    }
}
