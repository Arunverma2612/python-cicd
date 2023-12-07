pipeline {
    agent any

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image with Git commit as a tag
                    sh "docker build -t arul:$GIT_COMMIT ."
                }
            }
        }

        stage('Stop and Remove Existing Container') {
            steps {
                script {
                    // Stop and remove existing container named "arul"
                    sh "docker stop arul || true"
                    sh "docker rm arul || true"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the latest built image
                    sh "docker run -p 8081:8080 --name arul -d arul:$GIT_COMMIT"
                }
            }
        }
    }
}
