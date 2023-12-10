pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build your Docker image
                    docker.build('my-node-app', '.')
                }
            }
        }

        stage('Check Node.js Version') {
            steps {
                script {
                    // Run a Docker container from the built image
                    def nodeVersion = docker.image('my-node-app').inside {
                        // Run a command inside the Docker container
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
                // Clean up: Remove the Docker image after checking Node.js version
                cleanWs()
                docker.image('my-node-app').remove()
            }
        }
    }
}

