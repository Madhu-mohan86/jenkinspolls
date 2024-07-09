pipeline{
    agent{
        node{
            label "dockernode"
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages{
        stage('current_pwd_check'){
            steps{
                sh "ls -ltr"
            }
        }
        stage('check_java'){
            steps{
                sh "java -version"
            }
        }
        stage('execute'){
            steps{
                sh "java Helloworld.java"
            }
        }
    }
}