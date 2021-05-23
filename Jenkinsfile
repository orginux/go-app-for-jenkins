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
    }
}
