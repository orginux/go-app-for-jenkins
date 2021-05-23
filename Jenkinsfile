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
            agent {
                docker { image 'alpine/git' }
            }
            steps {
                sh 'echo Cloning..'
                sh 'git clone https://github.com/orginux/echopod.git'
            }
        }
    }
}
