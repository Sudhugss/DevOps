pipeline{
    tools{
        jdk 'myJdk'
        maven 'myMaven'
    }
    agent none
    stages {
        stage('Compile'){
            agent any
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            agent any
            steps{
                sh 'mvn test'
            }
            post{
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package'){
            agent {label 'win_slave'}
            steps{
                git 'https://github.com/Sudhugss/DevOps.git'
                bat 'mvn package'
            }
        }
    }
}
