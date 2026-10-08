pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                // Checkout code from your GitHub repository
                git branch: 'main', url: 'git@github.com:Mallikarjun46/JenkinsDocker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image using the Dockerfile in the repository
                    def app = docker.build("discoverdevops/sample-node-app")
                }
            }
        }
        stage('Deploy Docker Container on Jenkins Master') {
            steps {
                script {
                    // Pull the image that was built earlier (already present on Jenkins master)
                    sh '''
                    docker stop sample-node-app || true
                    docker rm sample-node-app || true
                    docker run -d --name sample-node-app -p 3000:3000 discoverdevops/sample-node-app:latest
                    '''
                }
            }
        }
    }
}

      
    
