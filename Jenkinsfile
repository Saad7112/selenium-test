pipeline {
    agent any

    
    stages {
        stage('Build and Deploy') {
            steps {
                script {
                    //sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh'
                    //sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash'
                    //sh 'source ~/.bashrc'
                    //sh 'nvm list-remote'    
                    //sh 'nvm install v20.14.0'
                    //sh 'apt install nodejs -y'
                    sh 'cd /var/lib/jenkins/workspace/Hello_test/sel-test'
                    sh 'ls'
                    sh 'node -v'
                    sh 'npm -v'
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
