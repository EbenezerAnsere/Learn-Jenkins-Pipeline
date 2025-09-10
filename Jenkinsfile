pipeline {
    agent any
    
    stages {
        stage('Run Docker') {
            agent {
                docker {
                    image 'node:14-alpine'
                    reuseNode true   // optional: mounts Jenkins workspace
                }
            }
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'echo "Running inside Node 14 Alpine container!"'
            }
        }
    }
}
pipeline {
    agent any
    
    stages {
        stage('Run Docker') {
            agent {
                docker {
                    image: 'node:14-alpine'
                    reuseNode true   // optional: mounts Jenkins workspace
                }
            }
            steps {
                sh 'node -v'
                sh 'npm -v'
                sh 'echo "Running inside Node 14 Alpine container!"'
            }
        }
        stage('Run Test'){
            steps{
                echo 'Running Test'
            }
        }
    }
}
