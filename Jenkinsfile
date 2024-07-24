pipeline {
    agent any
    tools {
        nodejs 'node' // Name of the Node.js installation you configured
    }

    
    stages {

            // SonarQube Analysis
        stage('SonarQube Analysis') {
            steps {
                script {
                    withSonarQubeEnv('sonar') {
                        dir('/var/lib/jenkins/workspace/Hello_test/sel-test') {
                            // Install Node.js dependencies
                            sh 'npm install'

                            // Run SonarScanner for JavaScript/TypeScript
                            def sonarScannerCmd = 'sonar-scanner'
                            withCredentials([string(credentialsId: 'sqp_48de73f589a5a77fb61623d9adf0a473000dce2d', variable: 'SONAR_TOKEN')]) {
                                // Set up the SonarQube analysis command with required parameters
                                sonarScannerCmd += " -Dsonar.projectKey=test-sonar"
                                sonarScannerCmd += " -Dsonar.sources=src"
                                sonarScannerCmd += " -Dsonar.host.url=http://localhost:9000"
                                sonarScannerCmd += " -Dsonar.login=${SONAR_TOKEN}"
                                sh "${sonarScannerCmd}"
                            }
                        }
                    }
                }
            }
        }





        
        stage('Build and Deploy') {
            steps {
                script {
                    // Make sure Docker is installed and running
                    bat 'docker compose up -d'
                    // Wait for Selenium Hub to be ready
                    retry(5) {
                        sleep(time: 10, unit: 'SECONDS')
                        
                    }
                    
                    // Build and run Docker Compose
                     bat 'node C:/ProgramData/Jenkins/test.js'
                }
            }
        }
    }
    

}
