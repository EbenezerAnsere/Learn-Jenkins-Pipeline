pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                    args '-e HOME=/var/lib/jenkins/workspace'
                }
            }
            steps {
                sh '''
                     ls -la
            node --version
            npm --version

            # force npm to use a local cache in the workspace
            mkdir -p .npm-cache
            npm config set cache $PWD/.npm-cache --global

            # clean install using lockfile
            npm ci --prefer-offline --no-audit

            # build project
            npm run build

            ls -la
                '''
            }
        }
        stage('Test') {
            steps {
                sh 'test -f build/index.html'
            }
        }
    }
}
