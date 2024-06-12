pipeline {
    agent any

    
    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    // Make sure Docker is installed and running
                    sh 'docker compose up'
                    
                    // Build and run Docker Compose
                    // sh 'docker-compose up -d --build
                     sh 'node test.js'
                }
            }
        }
    }
    

}
