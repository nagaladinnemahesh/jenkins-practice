pipeline {
    agent {
        docker {
            image 'node:14' // Use any Node.js version you need
        }
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm --version'
                sh 'node --version'
                // Add your build steps here
            }
        }
    }

    post {
        always {
            script {
                // Clean up: Remove the Docker image after the build
                cleanWs()
            }
        }
    }
}
