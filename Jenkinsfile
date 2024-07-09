pipeline{
    agent any
    stages{
        stage("build docker"){
            steps{
                script{
                docker.build("react/test")
                }
            }
        }
    }
}