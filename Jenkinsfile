pipeline {
    agent any
    stages {
        stage('check') {
            agent {
                docker { image 'golang' }
            }
            steps {
                sh 'go version'
            }
        }
        stage('clone') {
            steps {
                sh 'git clone https://github.com/orginux/echopod.git'
            }
        }
        stage('build') {
            agent {
                docker { image 'golang' }
            }
            environment {
                GO111MODULE = 'off'
                CGO_ENABLED = 0
                GOOS        = 'linux'
            }
            steps {
                sh 'go build -o echopod'
            }
        }
    }
}
