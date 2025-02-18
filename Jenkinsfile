pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Update the branch name here to 'main' if it's your default branch
                git branch: 'main', url: 'https://github.com/NinadDhuri/A-Dockerized-application-using-Jenkins-for-CI-CD.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t node-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 3000:3000 --name node-container node-app'
            }
        }
    }
}
