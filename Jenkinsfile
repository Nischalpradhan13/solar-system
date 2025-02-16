pipeline{
    agent any
    tools {
        maven 'Maven'
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
        
        
    }
   
}
