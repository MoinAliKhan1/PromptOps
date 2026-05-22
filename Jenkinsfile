pipeline {
    agent any

    stages {
        stage('Debug') {
            steps {
                sh 'echo "Jenkinsfile is executing"'
                sh 'whoami'
                sh 'pwd'
            }
        }
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
        stage('Push Docker Image') {
            steps {
                sh 'docker tag promptops-image moinalikhan/promptops-image:v1'
                sh 'docker push moinalikhan/promptops-image:v1'
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
