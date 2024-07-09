pipeline {
    agent any
    environment {
        DOCKER_IMAGE = 'madhu86/react'
    }
    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    // Build Docker image
                    def dockerImage = docker.build DOCKER_IMAGE
                }
            }
        }
        stage("Push Docker Image") {
            steps {
                script {
                    // Push Docker image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', "docker") {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
