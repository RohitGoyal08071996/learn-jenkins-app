pipeline {
    agent any

    environment {
        BUILD_NUMBER = '1'
    }

    stages {
        stage('Cleanup') {
            steps {
                echo 'Cleaning workspace...'
                cleanWs()
            }
        }

        stage('Build') {
            agent {
                docker {
                    image 'node:23-alpine3.20'
                    reuseNode true
                }
            }
            steps {
                echo 'Building...'
                sh '''
                    ls -la
                    node --version
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }
}
