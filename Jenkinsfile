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
                    
                    # fix npm cache permissions by using a local folder
                    npm config set cache $PWD/.npm-cache --global
                    
                    # clean install
                    npm ci
                    
                    # build project
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
        stage('Archive Build') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }
}
