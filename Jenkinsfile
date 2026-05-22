pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/MoinAliKhan1/PromptOps.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t promptops-image .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop promptops || true'
                sh 'docker rm promptops || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name promptops promptops-image'
            }
        }
    }
}
