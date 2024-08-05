pipeline {

    agent any;

    parameters {
        string(name: "DOCKER_IMAGE_INPUT", defaultValue: "madhu86/react", description: "Default Docker image")
    }

    environment {
        DOCKER_IMAGE = "${params.DOCKER_IMAGE_INPUT}"
    }

    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    // Build Docker image
                    dockerImage = docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage("Push Docker Image") {
            steps {
                script {
                    // Push Docker image to Docker Hub
                    docker.withRegistry('https://registry.hub.docker.com', 'docker') {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline successfully completed!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
