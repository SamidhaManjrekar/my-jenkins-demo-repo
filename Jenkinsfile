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
                sh 'docker run --rm jenkins-demo-app npm test || echo "No tests yet"'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:3000 --name jenkins-demo-container jenkins-demo-app'
            }
        }
    }
}