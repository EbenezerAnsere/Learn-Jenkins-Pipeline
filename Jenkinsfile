pipeline {
    agent any

    stages {
        stage('Build') {
            agent{
                docker{
                    // image 'node:18-alpine'
                    // args '-v /c/ProgramData/Jenkins/.jenkins/workspace:/workspace -w /workspace'
                    // reuseNode true
                    sh 'docker run -d -t \
                        -v /c/ProgramData/Jenkins/.jenkins/workspace:/workspace \
                        -w /workspace/learn-jenkins-app \
                        node:18-alpine'
                }
            }
            steps {
                sh ''' 
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
