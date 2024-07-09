pipeline{
    agent any
    stages{
        stage("build docker"){
            steps{
                docker.build("react/test")
            }
        }
    }
}