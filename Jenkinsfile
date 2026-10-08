pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                // Checkout code from your GitHub repository
                git branch: 'main', url: 'https://github.com/Mallikarjun46/JenkinsDocker.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image using the Dockerfile in the repository
                    sh 'docker build -t example1:latest .'
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
                    docker run -d --name sample-node-app -p 3000:3000 example1:latest
                    '''
                }
            }
        }
    }
}

      
    
