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
                powershell '''
                    # Build Docker image
                    docker build -t node-app .
                '''
            }
        }
        stage('Run Docker Container') {
            steps {
                powershell '''
                    # Run the Docker container
                    docker run -d -p 3000:3000 --name node-container node-app
                '''
            }
        }
    }
    post {
        always {
            powershell '''
                # Clean up Docker containers after the pipeline runs
                docker ps -q --filter "ancestor=node-app" | ForEach-Object { docker stop $_ }
                docker ps -aq --filter "ancestor=node-app" | ForEach-Object { docker rm $_ }
            '''
        }
    }
}
