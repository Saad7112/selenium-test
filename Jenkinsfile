pipeline {
    agent any

    
    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    sh 'cd /var/lib/jenkins/workspace/Hello_test/sel-test/'
                    sh 'npm init -y'
                    sh 'npm install express'
                    // Make sure Docker is installed and running
                    sh 'docker --version'
                    sh 'docker compose up'
                    
                    // Build and run Docker Compose
                    // sh 'docker-compose up -d --build
                     sh 'node test.js'
                }
            }
        }
    }
    

}
