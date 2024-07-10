def isDockerConfigured() {
    return Jenkins.instance.pluginManager.plugins.any { it.shortName == 'docker-plugin' && it.active }
}

pipeline {
    agent {
        // Use a Docker agent if Docker is configured, otherwise use any available agent
        label isDockerConfigured() ? 'docker' : ''
    }

    parameters {
        string(name: "DOCKER_IMAGE_INPUT", defaultValue: "madhu86/react", description: "Default Docker image")
    }

    environment {
        DOCKER_IMAGE = params.DOCKER_IMAGE_INPUT
    }

    triggers {
        pollSCM('0 0 */2 * * *') // Poll SCM every 2 hours
    }

    stages {
        stage("Build Docker Image") {
            steps {
                script {
                    // Build Docker image
                    dockerImage = docker.build DOCKER_IMAGE
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
