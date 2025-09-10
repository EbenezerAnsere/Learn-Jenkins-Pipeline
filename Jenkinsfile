pipeline {
    agent any
    
    stages {
        stage('Run Node 14 in Docker') {
            agent {
                docker {
                    image 'node:14-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'echo "Running inside Node 14 Alpine container!"'
            }
        }

        stage('Run Node 18 in Docker') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'echo "Running inside Node 18 Alpine container!"'
            }
        }

        stage('Run Test') {
            steps {
                echo 'Running Test'
            }
        }
    }
}
