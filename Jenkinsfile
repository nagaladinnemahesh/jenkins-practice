pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Assuming your code repository is Git. Adjust this as needed.
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build your project, replace 'mvn clean install' with your build command
                    sh 'mvn clean install'
                }
            }
        }
    }

    post {
        success {
            echo 'Build successful! Deploy or do additional tasks here.'
        }

        failure {
            echo 'Build failed! Take necessary actions.'
        }

        always {
            // Clean up or additional tasks that should run regardless of success or failure
        }
    }
}
