pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                cleanWs()   // requires "Workspace Cleanup" plugin
                checkout scm
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh '''
                    ls -la
                    node --version
                    npm --version
                    # configure npm to use a local cache folder in workspace
                    npm config set cache $PWD/.npm-cache --global
                    npm ci --no-cache
                    npm run build
                    ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                echo 'Test stage'
            }
        }
    }
}
