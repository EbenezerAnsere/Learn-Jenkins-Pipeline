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
                docker run hello
                    ls -la
                    node --version
                    npm --version
                    npm ci
                    npm run build
                    ls -la
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
