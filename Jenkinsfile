pipeline {
    agent any
    tools {
        nodejs 'node-23-8-0'
    }
    stages {
        stage("VM Node Version") {
            steps {
                sh '''
                    node -v
                    npm -v
                '''
            }
        }
        stage("Install Dependencies") {
            steps {
                sh 'npm install --no-audit'
            }
        }
    }
}
