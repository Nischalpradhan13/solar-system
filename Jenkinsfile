pipeline{
    agent any
    tools {
        nodejs 'node-23-8-0'
    }
    stages{
        stage("Vm   Node Version"){
            steps{
                sh '''
                    node -v
                    npm -v
                '''
            }
            
        }
        
        
    }
    stages{
        stage("Install Dependencies"){
            steps{
                sh 'npm install --no-audit'
            }
            
        }
        stage("Install Dependencies"){
            steps{
                sh '''
                   npm audit --audit-level=critical
                   echo $?
                '''
            }
            
        }
        
    }
   
}
