pipeline {
    agent none
    stages {
        stage('Jekyll Build') {
            agent {
                docker {
                    image 'docker:18.09'
                    args '-u root:sudo'
                }
            }
            steps {
                checkout scm
                sh 'whoami'
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
