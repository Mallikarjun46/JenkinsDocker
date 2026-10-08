pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Mallikarjun46/JenkinsDocker.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t example1:latest .'
            }
        }

        stage('Deploy Docker Container') {
            steps {
                sh '''
                    docker rm -f example1 || true

                    docker run -d \
                        --name example1 \
                        -p 5000:5000 \
                        example1:latest
                '''
            }
        }
    }
}

      
    
