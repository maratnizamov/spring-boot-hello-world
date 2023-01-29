pipeline {
    agent any
    tools{
        maven 'My_Maven_for_Jenkins'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/maratnizamov/spring-boot-hello-world']])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    bat 'docker build --build-arg JAR_FILE=target/spring-boot-2-hello-world-1.0.2-SNAPSHOT.jar -t maratnizamov/app .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                   bat 'docker login -u maratnizamov -p %dockerhubpwd%'
}
                   bat 'docker push maratnizamov/app'
                }
            }
        }

    }
}