pipeline{
    agent any

    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker')
    }
    stages{
        stage("build docker"){
            steps{
                def app=docker.build("madhu86/react")
            }
        }
        stage("push the image"){
            steps{
                docker.withRegistry("https://hub.docker.com/r/madhu86/react",DOCKERHUB_CREDENTIALS){
                    app.push()
                }
            }
        }
    }
}