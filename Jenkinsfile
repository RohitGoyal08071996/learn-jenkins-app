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
