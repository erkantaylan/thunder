pipeline {
    agent any

    stages {
        stage('Build and Run with Docker Compose') {
            steps {
                script {
                    // Ensure Docker is available
                    sh 'docker --version'
                    
                    // Run Docker Compose to build and start services
                    sh 'docker-compose -f compose.yaml up --build -d'
                }
            }
        }
    }

    post {
        always {
            // Stop and remove containers after the job completes
            script {
                sh 'docker-compose -f compose.yaml down'
            }
        }
    }
}
