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
                echo 'Building new laptop...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
    }
}
