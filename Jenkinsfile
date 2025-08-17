pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'your-credential-id', url: 'https://github.com/your-username/my-jenkins-demo-repo.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:3000 jenkins-demo-app'
            }
        }
    }
}