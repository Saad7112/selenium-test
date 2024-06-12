pipeline {
    agent any

    environment {
        NVM_DIR = "${WORKSPACE}/.nvm"
    }

    stages {
        stage('Setup Node.js') {
            steps {
                script {
                    sh '''
                        # Install NVM if not already installed
                        if [ ! -d "$NVM_DIR" ]; then
                            curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
                        fi
                        
                        # Load NVM and install Node.js
                        export NVM_DIR="${WORKSPACE}/.nvm"
                        [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                        nvm install 20
                        nvm use 20
                    '''
                }
            }
        }
        
        stage('Build and Deploy') {
            steps {
                script {
                    sh '''
                        # Load NVM and use Node.js
                        export NVM_DIR="${WORKSPACE}/.nvm"
                        [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                        nvm use 20
                        
                        # Navigate to the workspace directory
                        cd /var/lib/jenkins/workspace/Hello_test/sel-test/
                        
                        # Initialize npm project and install dependencies
                        npm init -y
                        npm install express
                        
                        # Verify Node.js and npm versions
                        node -v
                        npm -v

                        # Make sure Docker is installed and running
                        docker --version
                        
                        # Build and run Docker Compose
                        docker compose up -d --build
                        
                        # Run test script
                        node test.js
                    '''
                }
            }
        }
    }
    
    post {
        always {
            script {
                sh '''
                    # Load NVM and use Node.js
                    export NVM_DIR="${WORKSPACE}/.nvm"
                    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
                    nvm use 20
                    
                    # Navigate to the workspace directory
                    cd /var/lib/jenkins/workspace/Hello_test/sel-test/
                    
                    # Clean up Docker Compose containers
                    docker compose down
                '''
            }
        }
    }
}
