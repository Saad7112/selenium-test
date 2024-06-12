pipeline {
    agent any

    environment {
        NVM_DIR = "${WORKSPACE}/.nvm"
        NVM_SCRIPT = "source ${NVM_DIR}/nvm.sh"
    }

    stages {
        stage('Setup Node.js') {
            steps {
                script {
                    sh '''
                        curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
                        export NVM_DIR="${WORKSPACE}/.nvm"
                        [ -s "${NVM_DIR}/nvm.sh" ] && \. "${NVM_DIR}/nvm.sh"
                        nvm install 20
                    '''
                }
            }
        }
        
        stage('Build and Deploy') {
            steps {
                script {
                    sh '''
                        export NVM_DIR="${WORKSPACE}/.nvm"
                        [ -s "${NVM_DIR}/nvm.sh" ] && \. "${NVM_DIR}/nvm.sh"
                        nvm use 20
                        cd /var/lib/jenkins/workspace/Hello_test/sel-test
                        ls
                        npm init -y
                        npm install express
                        docker compose up 
                        
                    '''
                }
            }
        }
    }

   
}
