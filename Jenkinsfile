pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('my-node-app', '.')
                }
            }
        }

        stage('Check Node.js Version') {
            steps {
                script {
                    def nodeVersion = docker.image('my-node-app').inside {
                        sh(script: 'node --version', returnStatus: true).trim()
                    }

                    echo "Node.js version in the Docker image: $nodeVersion"
                }
            }
        }
    }
    
    post {
        always {
            script {
                cleanWs()
                docker.image('my-node-app').remove()
            }
        }
    }
}
