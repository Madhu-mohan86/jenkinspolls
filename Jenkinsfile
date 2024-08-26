pipeline {
    agent any

    parameters {
        choice(name: 'DOCKER_IMAGE_INPUT', choices: [
            'techeunimart/buyerapp.bullmq',
            'techeunimart/buyerapp.elastic',
            'techeunimart/buyerapp.kafka',
            'techeunimart/buyerapp.onsearch',
            'techeunimart/buyerapp.redis',
            'techeunimart/buyerapp.schedular',
            'techeunimart/sellerapp.bullmq',
            'techeunimart/sellerapp.kafka',
            'techeunimart/sellerapp.schedular'
        ], description: 'Docker repo where the image needs to be pushed')
        
        choice(name: 'DOCKER_FILE_INPUT', choices: [
            'Dockerfile.BuyerApp.bullmq',
            'Dockerfile.BuyerApp.elastic',
            'Dockerfile.BuyerApp.kafka',
            'Dockerfile.BuyerApp.onsearch',
            'Dockerfile.BuyerApp.redis',
            'Dockerfile.BuyerApp.schedular',
            'Dockerfile.SellerApp.bullmq',
            'Dockerfile.SellerApp.kafka',
            'Dockerfile.SellerApp.schedular'
        ], description: 'Docker file for building the image')
    }

    environment {
        DOCKER_IMAGE = "${params.DOCKER_IMAGE_INPUT}"
        DOCKER_FILE = "${params.DOCKER_FILE_INPUT}"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    dockerImage = docker.build("${DOCKER_IMAGE}", "-f ${DOCKER_FILE} .")
                }
            }
        }

        stage('Push Docker Image') {
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
            echo 'Pipeline successfully completed!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
