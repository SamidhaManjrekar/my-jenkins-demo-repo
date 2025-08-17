pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SamidhaManjrekar/my-jenkins-demo-repo.git',
                    credentialsId: 'github-creds'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t jenkins-demo-app .'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:3000 jenkins-demo-app'
            }
        }
    }
}