pipeline {
    agent any

    environment {
        BUILD_NUMBER = '1'
    }

    stages {
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
                    npm --version
                    npm ci
                    npm run build
                    ls -al
                '''
            }
        }

        stage('Test') {
            agent {
                docker {
                    image 'node:23-alpine3.20'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    echo "Testing..."
                    test -f build/index.html
                    npm test
                '''
            }
        }

        stage('Parallel Tests') {
            parallel {
                stage('Unit Test') {
                    agent {
                        docker {
                            image 'node:23-alpine3.20'
                            reuseNode true
                        }
                    }
                    steps {
                        echo 'Unit Testing...'
                        sh '''
                            npm test
                        '''
                    }
                }

                stage('Integration Test') {
                    agent {
                        docker {
                            image 'node:23-alpine3.20'
                            reuseNode true
                        }
                    }
                    steps {
                        echo 'Integration Testing...'
                        sh '''
                            npm test
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            junit 'test-results/**/*.xml'
        }
    }
}
