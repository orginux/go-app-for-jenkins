pipeline {
    agent { docker { image 'golang' } }
    stages {
        stage('build') {
            steps {
                sh 'go version'
            }
        }
        stage('test') {
            steps {
                sh 'echo Hello'
            }
        }
    }
}
