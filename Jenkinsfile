pipeline {

    agent any;

    parameters {
         choice(name: "DOCKER_IMAGE_INPUT", choices: ['techeunimart/reacttesting', 'techeunimart/bullmq', 'techeunimart/kafka'], description: "Default Docker image")
        choice(name: "DOCKER_FILE_INPUT", choices: ['Dockerfile.alpine', 'Dockerfile.web', 'Dockerfile.data'], description: "Default Docker file")
    }

    environment {
        DOCKER_IMAGE = "${params.DOCKER_IMAGE_INPUT}"
        DOCKER_FILE= "${params.DOCKER_FILE_INPUT}"
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
