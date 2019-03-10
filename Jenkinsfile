pipeline {
    agent none
    stages {
        stage('Jekyll Build') {
            agent {
                docker 'docker:18.09'
            }
            steps {
                checkout scm
                sh 'apk add --no-cache make'
                sh 'make build'
            }
        }
        stage('Deploy') {
            agent {
                docker 'ditemikuthesisdemo/deploy:1.0'
            }
            steps {
                sh 'make deploy'
            }
        }
    }
}
