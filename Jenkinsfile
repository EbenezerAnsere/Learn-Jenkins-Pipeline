pipeline {
    agent any
    
    stages{
        stage('Run Docker'){
            agent{
                docker{
                    image: 'node:14-alpine'
                }
            }
        }
    }

  
}
