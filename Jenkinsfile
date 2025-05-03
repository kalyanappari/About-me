pipeline {
    agent any

    environment {
        IMAGE_NAME = 'kalyan3003/simple-html-site'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/kalyanappari/About-me.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
