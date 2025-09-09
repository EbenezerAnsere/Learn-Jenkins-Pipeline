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
            agent{
                docker{
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh ''' 
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                '''
              
            }
        }
        stage('Test'){
            steps{
                echo 'Test stage'
            }
        }
    }
}
