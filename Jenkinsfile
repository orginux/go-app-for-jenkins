pipeline {
    agent { docker { image 'golang' } }
    stages {
        stage('build') {
            steps {
                sh 'go version'
            }
        }
        stage('test') {
            agent { docker { image 'alpine/git' } }
            steps {
                sh 'git clone https://github.com/orginux/echopod.git'
            }
        }
    }
}
