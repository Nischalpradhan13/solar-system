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

        stage("NPM install") {
            steps {
                sh 'npm install --no-audit'
            }
        }

        stage("Fix Dependencies") {
            steps {
                sh 'npm audit fix || true'  // Fix vulnerabilities but continue even if it fails
            }
        }

        stage("Dependency Check") {
            steps {
                sh 'npm install --no-audit'
            }
        }

        stage("Dependency Scanning") {
            parallel {
                stage("Security Audit") {
                    steps {
                        sh '''
                            npm audit --audit-level=critical
                            echo $?
                        '''
                    }
                }

                stage("OWASP Dependency Check") {
                    steps {
                        dependencyCheck additionalArguments: '''
                            --scan './'
                            --out './'
                            --format 'ALL'
                            --prettyPrint''', 
                            odcInstallation: 'OWASP-DepCheck-10'
                    }
                }
            }
        }
    }
}
