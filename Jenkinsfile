pipeline {
    agent any

    environment {
        IMAGE_NAME = "demo-jenkins-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/SamidhaManjrekar/my-jenkins-demo-repo.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                dir('app') {
                    sh 'docker build -t $IMAGE_NAME:$BUILD_NUMBER .'
                }
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker rm -f demo-container || true'
                sh 'docker run -d --name demo-container -p 8081:80 $IMAGE_NAME:$BUILD_NUMBER'
            }
        }
    }
}