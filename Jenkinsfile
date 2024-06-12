pipeline {
    agent any
    tools {
        nodejs 'node' // Name of the Node.js installation you configured
    }

    
    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    // Make sure Docker is installed and running
                    sh 'docker compose up -d'
                    // Wait for Selenium Hub to be ready
                    retry(5) {
                        sleep(time: 10, unit: 'SECONDS')
                        
                    }
                    
                    // Build and run Docker Compose
                    // sh 'docker-compose up -d --build
                     sh 'node /home/new/saad/Selenium/test.js'
                }
            }
        }
    }
    

}
