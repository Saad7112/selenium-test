pipeline {
    agent any
    stages {
        stage('Setup Environment') {
            steps {
                script {
                    // Install the latest Node.js and npm
                    sh '''
                        curl -fsSL https://deb.nodesource.com/setup_current.x | sudo -E bash -
                        sudo apt-get install -y nodejs
                    '''
                    
                    // Verify installation
                    sh 'node --version'
                    sh 'npm --version'
                }
            }
        }


    
    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    sh 'npm init -y'
                    sh 'npm install express'
                    // Make sure Docker is installed and running
                    sh 'docker --version'
                    sh 'docker compose up'
                    
                    // Build and run Docker Compose
                    // sh 'docker-compose up -d --build
                }
            }
        }
    }
    
    post {
        always {
            // Clean up Docker Compose containers
            sh 'node test.js'
        }
    }
}
